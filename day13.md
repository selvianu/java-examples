#Day13

* In the below example, we can learn 
  * Encapsulation
package com.chainsys.w3.day14;

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

````J