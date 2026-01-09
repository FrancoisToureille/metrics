# metrics Exercice 4 François TOUREILLE
## 3 issues found by SonarQube
### On a ce code alors que fileScanner est null : Bank Account:167
```java
FileInputStream fis = null;
		Scanner fileScanner = null;
		try {
			while (fileScanner.hasNextLine()) {
				fis = new FileInputStream(text);
				fileScanner = new Scanner(fis);
```
### On a cette variable `success` que l'on n'utilise plus suite à l'exercice 2, donc on doit la supprimer : BankAccount:22

`Remove this unused "success" private field.sonarqube(java:S1068)`
```java
public class BankAccount {

	private Person accountHolder;
	private double balance = 0;
	private String dateCreated;
	private double withdrawLimit = 0;
	private boolean success;
	private double initMoneyAmount = 0;
	private int accountNumber = 0;
	private double amountWithdrawn = 0;

```

### Enfin, on peut supprimer la variable `bankInfos` étant donné que l'on peut faire directement un return:BankAccount:213

`Immediately return this expression instead of assigning it to the temporary variable "bankInfo"`
```java
public String toString() {

		String bankInfo = "Your Account number is " + accountNumber + " " + "Your Balance is: " + balance + " "
				+ "Date account created is: " + dateCreated + " " + "Withdraw limit is: " + withdrawLimit + " "
				+ "Your account holder info is: " + accountHolder;

		return bankInfo;
```

## Fixes
### Bank Account:167
```java
FileInputStream fis = null;
		Scanner fileScanner = null;
		try {
			fis = new FileInputStream(text);
			fileScanner = new Scanner(fis);
			while (fileScanner.hasNextLine()) {
```

### Bank Account:22
```java
public class BankAccount {
	private Person accountHolder;
	private double balance = 0;
	private String dateCreated;
	private double withdrawLimit = 0;
	private double initMoneyAmount = 0;
	private int accountNumber = 0;
	private double amountWithdrawn = 0;

```
Les erreurs disparaissent bien.

### Do SonarLint issues appear more often in the classes with higher WMC / CBO you saw earlier, or not really?
Non pas vraiment car Person a un taux élevé de  WMC / CBO mais comporte très peu de warning, le soucis est surtout du côté de la manière dont le code a été développé
  ```
