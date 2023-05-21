#####Validaion
```java
package com.practice;

import java.util.regex.Matcher;
import java.util.regex.Pattern;


public class Validator {

	public static void main(String[] args) {
		Boolean isNameValid = nameValidation("priyadharshini");
		System.out.println(isNameValid);
		System.out.println(nameValidation("234567"));
		System.out.println(nameValidation("@#^%$^"));
		System.out.println(nameValidation("NILAN"));
		System.out.println("Password Valid: " + passwordValidation("Nilan123#"));
		System.out.println("Password Validity: " + passwordValidation("Nilan123"));
		System.out.println("Valid Mobile number" + phoneNumberValidation(8965432109l));
		System.out.println("Invalid Mobile number" + phoneNumberValidation(8965109l));
		System.out.println("Valid mail id: " + emailValidation("nouser@testmail.com"));
		System.out.println("Valid mail id Check: " + emailValidation("nousertestmail.com"));
		System.out.println(aadhaarValidation(340956871200l));
		System.out.println(aadhaarValidation(3409568710l));

	}

	public static Boolean nameValidation(String userName) {
		String regex = "[a-zA-Z]{4,}";// Initialize the format
		Pattern p = Pattern.compile(regex);
		Matcher valid = p.matcher(userName);
		Boolean ans = valid.matches();
		if (Boolean.FALSE.equals(ans)) {
			String errorMessage = "Min 4 character And No Special Character,No Numbers ";
			return false;
		}
		return true;
	}

	public static Boolean passwordValidation(String password) {
		String regex = ".[A-Za-z0-9]{1,}[@#$!%^&?><]{1,}.*";// Initialize the format
		Pattern p = Pattern.compile(regex);
		Matcher valid = p.matcher(password);
		Boolean ans = valid.matches();
		if (Boolean.FALSE.equals(ans)) {
			String errorMessage = "Min 5 Character And Max 20 One Captial Letter And Numbers,Special Characters";
			return false;
		}
		return true;
	}

	public static Boolean phoneNumberValidation(Long mobNum) {
		String number = Long.toString(mobNum);
		String regex = "^\\d{10}$";// Initialize the format
		Pattern p = Pattern.compile(regex);
		Matcher valid = p.matcher(number);
		Boolean ans = valid.matches();
		if (Boolean.FALSE.equals(ans)) {
			String errorMessage = "Maxmium 10 Number";
			return false;
		}
		return true;
	}

	public static Boolean emailValidation(String emailId) {
		String regex = "^(.+)@(.+)$";// Initialize the format
		Pattern p = Pattern.compile(regex);
		Matcher valid = p.matcher(emailId);
		Boolean ans = valid.matches();
		if (Boolean.FALSE.equals(ans)) {
			String errorMessage = "An Email Address must Contain @ symbol";
			return false;
		}
		return true;
	}

	public Boolean salaryValidation(Integer salary) {
		String number = Integer.toString(salary);
		String regex = "^\\d{5}$";// Initialize the format
		Pattern p = Pattern.compile(regex);
		Matcher valid = p.matcher(number);
		Boolean ans = valid.matches();
		if (Boolean.FALSE.equals(ans)) {
			String errorMessage = "Maxmium 5 digits";
			return false;
		}
		return true;
	}

	public Boolean accountNo(Long accountNo) {
		String num = accountNo.toString();
		String regex = "^(\\d{10}|\\d{13}|\\d{15}|\\d{17})$";// Initialize the format
		Pattern p = Pattern.compile(regex);
		Matcher valid = p.matcher(num);
		Boolean ans = valid.matches();
		if (Boolean.FALSE.equals(ans)) {
			String errorMessage = "Invalid Account number, account number should be 10 or 13 or 15 or 17 digits";
			return false;
		}
		return true;
	}

	public static String aadhaarValidation(Long aadhaarNum) {
		String number = Long.toString(aadhaarNum);
		String regex = "^\\d{12}$";// Initialize the format
		Pattern p = Pattern.compile(regex);
		Matcher valid = p.matcher(number);
		Boolean ans = valid.matches();
		if (Boolean.FALSE.equals(ans)) {
			String errorMessage = "Enter Valid 12 Digit Aadhar Number!";
			return errorMessage;
		}
		return "valid AADHAR number";
	}

}
```