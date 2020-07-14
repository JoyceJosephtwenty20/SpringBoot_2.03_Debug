"# SpringBoot_2.03_Debug" 


-------------------------------------------------------------------------------------------------------------------

//Person.java

public class Person {
private String firstName;
private String lastName;
private String email;
private int phoneNumber;
private String address;
private String city;
private String state;
private int zipcode;

public Person() {}

public String getFirstName() {
return firstName;
}

public void setFirstName(String firstName) {
this.firstName = firstName;
}

public String getLastName() {
return lastName;
}

public void setLastName(String lastName) {
this.lastName = lastName;
}

public String getEmail() {
return email;
}

public void setEmail(String email) {
this.email = email;
}

public int getPhoneNumber() {
return phoneNumber;
}

public void setPhoneNumber(int phoneNumber) {
this.phoneNumber = phoneNumber;
}

public String getAddress() {
return address;
}

public void setAddress(String address) {
this.address = address;
}

public String getCity() {
return city;
}

public void setCity(String city) {
this.city = city;
}

public String getState() {
return state;
} 

public void setState(String state) {
this.state = state;
}

public int getZipcode() {
return zipcode;
}

public void setZipcode(int zipcode) {
this.zipcode = zipcode;
}
} 


-------------------------------------------------------------------------------------------------------------------

// HomeController.java

@Controller
public class HomeController {

@GetMapping("/loadPersonForm")
public String loadPersonForm(Model model) {
model.addAttribute("person", new Person());
return "personForm"

}

@PostMapping("/processPersonForm")
public String processPersonForm(@ModelAttribute Person person, Model model) {

model.addAttribute("personWData", person);
return "confirmPerson";
}

}


-------------------------------------------------------------------------------------------------------------------

// personForm.html
<DOCType html>
<html lang="en" xmlns:th="www.t.com">
<head>
<title> Person Form </title>
</head>
<body>
<form action="#" th:action="@{/loadPersonForm}" th:objet="#{person}" method="post">

First name: <input type="text" th:field="*{firstName}"> <br>
Last name: <input type="text" th:field="*{lastName}"> <br>
Email address: <input type="email" th:field="*{email}"> <br>
Phone number: <input type="text" th:field="*{phoneNumber}"> <br>
Address: <input type="text" th:field="*{address}"> <br>
City: <input type="text" th:field="*{city}"> <br>
State: <input type="text" th:field="*{state}"> <br>
Zipcode: <input type="text" th:field="*{zipcode}"> <br>

</form>
</body>
</html> 

-------------------------------------------------------------------------------------------------------------------

// confirmPerson.html

<DOCType html>
<html lang="en" xmlns:th="www.t.com">
<head>
<title> Person Confirm </title>
</head>
<body>
<p th:inline="text">
First name: [[${personWData.firstName}]]
Last name: [[${personWData.lastName}]]
Email address: [[${personWData.email}]]
Phone number: [[${personWData.phoneNumber}]]
Address: [[${personWData.address}]]
City: [[${personWData.city}]]
State: [[${personWData.state}]]
Zipcode: [[${personWData.zipcode}]]
</p>
</body>
</html> 
