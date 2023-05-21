#### Java Stream API
The exercises are based on a data model — customer, order and product. Refer to the entity relationship diagram below, customers can place multiple orders and so it is a one-to-many relationship while the relationship between products and orders is many-to-many.
#### Obtain a list of products belongs to category “Books” with price > 100
```java
List<Product> result = productRepo.findAll()
  .stream()
  .filter(p -> p.getCategory().equalsIgnoreCase("Books"))
  .filter(p -> p.getPrice() > 100)
  .collect(Collectors.toList());
  ```
#### Obtain a list of order with products belong to category “Baby”
```java
  List<Order> result = orderRepo.findAll()
        .stream()
        .filter(o -> 
          o.getProducts()
          .stream()
          .anyMatch(p -> p.getCategory().equalsIgnoreCase("Baby"))
        )
        .collect(Collectors.toList()); 
```
#### Obtain a list of product with category = “Toys” and then apply 10% discount    
```java
List<Product> result = productRepo.findAll()
        .stream()
        .filter(p -> p.getCategory().equalsIgnoreCase("Toys"))
        .map(p -> p.withPrice(p.getPrice() * 0.9))
        .collect(Collectors.toList());  
```
#### Obtain a list of products ordered by customer of tier 2 between 01-Feb-2021 and 01-Apr-2021
```java
List<Product> result = orderRepo.findAll()
  .stream()
  .filter(o -> o.getCustomer().getTier() == 2)
  .filter(o -> o.getOrderDate().compareTo(LocalDate.of(2021, 2, 1)) >= 0)
  .filter(o -> o.getOrderDate().compareTo(LocalDate.of(2021, 4, 1)) <= 0)
  .flatMap(o -> o.getProducts().stream())
  .distinct()
  .collect(Collectors.toList());
  ```
#### Get the cheapest products of “Books” category
```java 
Optional<Product> result = productRepo.findAll()
        .stream()
        .filter(p -> p.getCategory().equalsIgnoreCase("Books"))
        .sorted(Comparator.comparing(Product::getPrice))
        .findFirst();
```
#### Get the 3 most recent placed order
```java
  List<Order> result = orderRepo.findAll()
        .stream()
        .sorted(Comparator.comparing(Order::getOrderDate).reversed())
        .limit(3)
        .collect(Collectors.toList());
```
#### Get a list of orders which were ordered on 15-Mar-2021, log the order records to the console and then return its product list
```java
List<Product> result = orderRepo.findAll()
    .stream()
    .filter(o -> o.getOrderDate().isEqual(LocalDate.of(2021, 3, 15)))
    .peek(o -> System.out.println(o.toString()))
    .flatMap(o -> o.getProducts().stream())
    .distinct()
    .collect(Collectors.toList());
```
#### Calculate total lump sum of all orders placed in Feb 2021
```java
  Double result = orderRepo.findAll()
    .stream()
    .filter(o -> o.getOrderDate().compareTo(LocalDate.of(2021, 2, 1)) >= 0)
    .filter(o -> o.getOrderDate().compareTo(LocalDate.of(2021, 3, 1)) < 0)
    .flatMap(o -> o.getProducts().stream())
    .mapToDouble(p -> p.getPrice())
    .sum();
```
#### Calculate order average payment placed on 14-Mar-2021
```java
Double result = orderRepo.findAll()
        .stream()
        .filter(o -> o.getOrderDate().isEqual(LocalDate.of(2021, 3, 15)))
        .flatMap(o -> o.getProducts().stream())
        .mapToDouble(p -> p.getPrice())
        .average().getAsDouble();
```
#### Obtain a collection of statistic figures (i.e. sum, average, max, min, count) for all products of category “Books”
```java
  DoubleSummaryStatistics statistics = productRepo.findAll()
    .stream()
    .filter(p -> p.getCategory().equalsIgnoreCase("Books"))
    .mapToDouble(p -> p.getPrice())
    .summaryStatistics();
  
  System.out.println(String.format("count = %1$d, average = %2$f, max = %3$f, min = %4$f, sum = %5$f", 
    statistics.getCount(), statistics.getAverage(), statistics.getMax(), statistics.getMin(), statistics.getSum())));
```
#### Obtain a data map with order id and order’s product count
```java
Map<Long, Integer>  result = orderRepo.findAll()
        .stream()
        .collect(
            Collectors.toMap(
                order -> order.getId(),
                order -> order.getProducts().size()
                )
            );
```
####  Produce a data map with order records grouped by customer
```java
Map<Customer, List<Order>> result = orderRepo.findAll()
        .stream()
        .collect(
            Collectors.groupingBy(Order::getCustomer)
            );
```
#### Produce a data map with order record and product total sum
```java
Map<Order, Double> result = orderRepo.findAll()
        .stream()
        .collect(
          Collectors.toMap(
              Function.identity(), 
              order -> order.getProducts().stream()
                    .mapToDouble(p -> p.getPrice()).sum()
            ) 
          );
```
#### Obtain a data map with list of product name by category
```java
Map<String, List<String>> result = productRepo.findAll()
        .stream()
        .collect(
            Collectors.groupingBy(
                Product::getCategory,
                Collectors.mapping(product -> product.getName(), Collectors.toList()))
            );
```
#### Get the most expensive product by category
```java
Map<String, Optional<Product>> result = productRepo.findAll()
        .stream()
        .collect(
            Collectors.groupingBy(
                Product::getCategory,
                Collectors.maxBy(Comparator.comparing(Product::getPrice)))
```
