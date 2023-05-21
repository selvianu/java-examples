#Day15

* In the below example, we can learn 
  * Abstraction - ArrayList

````java
package com.chainsys.w3.day15;

public class Hotel {
	public Integer id;
	public String name;
	private String location;
	public Long phoneNumber;
	public Boolean dining;

	public Integer getId() {
		return id;
	}

	public void setId(Integer id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public Long getPhoneNumber() {
		return phoneNumber;
	}

	public void setPhoneNumber(Long phoneNumber) {
		this.phoneNumber = phoneNumber;
	}

	public Boolean getDining() {
		return dining;
	}

	public void setDining(Boolean dining) {
		this.dining = dining;
	}

	public Hotel() {
	}

	public String getLocation() {
		return location;
	}

	public void setLocation(String location) {
		this.location = location;
	}

	public Hotel(Integer id, String name, String location, Long phoneNumber, Boolean dining) {
		this.id = id;
		this.name = name;
		this.location = location;
		this.phoneNumber = phoneNumber;
		this.dining = dining;
	}

	public Boolean nameValidation(String name) {
		if (name.trim().length() > 5)
			return true;
		else
			return false;
	}

	@Override
	public String toString() {
		return "Hotel [id=" + id + ", name=" + name + ", location=" + location + ", phoneNumber=" + phoneNumber
				+ ", dining=" + dining + "]";
	}

}
````
````java
package com.chainsys.w3.day15;

import java.util.List;

public interface HotelInterface {
	//access-specifer returnType nameOfMethod(args)-verb-actionword
	public String addBranch(String branchName) throws Exception;
	public List listOfBranches();
	public List branchWithDining();

}
````
````java
package com.chainsys.w3.day15;

import java.util.ArrayList;
import java.util.List;

public class HoteImpl implements HotelInterface {
	Hotel h = new Hotel();

	@Override
	public List listOfBranches() {
		ArrayList branchList = new ArrayList();
		branchList.add("4,Chennai");
		branchList.add("1,Delhi");
		branchList.add("2,Madurai");
		branchList.add("5,Chennai");
		branchList.add("3,Chennai");
		return branchList;
	}

	@Override
	public String addBranch(String branchName) throws Exception {
		Boolean nameValidation = h.nameValidation(branchName);
		if (nameValidation == true)
			return branchName;
		else
			throw new Exception("Invalid branch name");
	}

	@Override
	public List branchWithDining() {
		ArrayList<Hotel> diningHotelList = new ArrayList();

		ArrayList<Hotel> hotellist = new ArrayList();
		Hotel h1 = new Hotel(109, "A2B", "Chennai", 45678l, true);
		Hotel h2 = new Hotel(76, "KFC", "Moggapair", 2378l, false);

		hotellist.add(h1);
		hotellist.add(h2);
		ArrayList<Hotel> hotellist2 = new ArrayList();
		Hotel h12 = new Hotel(78, "Anjappar", "Chennai", 45678l, true);
		Hotel h22 = new Hotel(90, "MadrasDosa", "Moggapair", 2378l, false);
		hotellist2.add(h12);
		hotellist2.addAll(hotellist);
		hotellist2.add(h22);
		for (Hotel hotel : hotellist2) {
			if (hotel.getDining() == true) {
				System.out.println("Adding into list");
				diningHotelList.add(hotel);
			} else
				System.out.println("No dining available");
		}
		return diningHotelList;

		// return hotellist2;
	}

}
````
````java
package com.chainsys.w3.day15;

import java.util.List;
import java.util.Scanner;

public class TestHotel {

	public static void main(String[] args) throws Exception {
		Hotel h = new Hotel();

		HoteImpl hotel = new HoteImpl();
	/*
		 * Scanner s = new Scanner(System.in);
		 * System.out.println("Enter location of new branch"); String branch = s.next();
		 * 
		 * // h.location = branch; h.setLocation(branch);
		 * System.out.println("Enter location of new branch"); String branch1 =
		 * s.next();
		 * 
		 * System.out.println(hotel.addBranch("Ambattur"));
		 * System.out.println(hotel.addBranch(branch));
		 * 
		 * // System.out.println(hotel.addBranch(h.location));
		 * //System.out.println(hotel.addBranch(h.getLocation()));// Encapsulated
		 * 
		 * System.out.println(hotel.addBranch(branch1));
		 * 
		 * List listOfBrach = hotel.listOfBranches(); System.out.println(listOfBrach);
		 */
System.out.println(hotel.branchWithDining());
	}

}
````