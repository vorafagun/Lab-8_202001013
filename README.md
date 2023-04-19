# Lab-8_202001013

## Creating test cases for `Boa` class
```
public class BoaTest {

  @Test
  public void testIsHealthyWithFavoriteFood() {
    Boa boa = new Boa("Bob", 10, "granola bars");
    assertTrue(boa.isHealthy());
  }

  @Test
  public void testIsHealthyWithoutFavoriteFood() {
    Boa boa = new Boa("Sally", 8, "mice");
    assertFalse(boa.isHealthy());
  }

  @Test
  public void testFitsInCageWithExactLength() {
    Boa boa = new Boa("Charlie", 6, "chicken");
    assertTrue(boa.fitsInCage(6));
  }

  @Test
  public void testFitsInCageWithLargerCage() {
    Boa boa = new Boa("Lucy", 5, "rats");
    assertTrue(boa.fitsInCage(10));
  }

  @Test
  public void testFitsInCageWithSmallerCage() {
    Boa boa = new Boa("Frank", 4, "eggs");
    assertFalse(boa.fitsInCage(3));
  }
}

```
In the above test cases, we test the `isHealthy()` method with a `Boa` instance with its favorite food and without its favorite food. We also test the `fitsInCage(int)` method with a `Boa` instance whose length exactly matches the cage length,
a `Boa` instance whose length is smaller than the cage length, and a `Boa` instance whose length is larger than the cage length.

## `Boa` class with the `setup()` method
Sure, here's an updated version of the BoaTest class with the setUp() method modified as requested:
```
public class BoaTest {

  private Boa jen;
  private Boa ken;

  @Before
  public void setUp() throws Exception {
    jen = new Boa("Jennifer", 2, "grapes");
    ken = new Boa("Kenneth", 3, "granola bars");
  }

  // add additional test methods here
}
```
With this modification, the `setUp()` method now initializes two `Boa` objects named `jen` and `ken` which can be used in the test methods. The `@Before` annotation ensures that the `setUp()` method is run before each test method is executed, so the `jen` and `ken` objects will be available to all the test methods in the class.

## Adding new method and test method in `Boa` class
Sure, here's an updated version of the `Boa` class with the `lengthInInches()` method added:
```
public class Boa {
  private String name;
  private int length; // the length of the boa, in feet
  private String favoriteFood;

  public Boa (String name, int length, String favoriteFood){
    this.name = name;
    this.length = length;
    this.favoriteFood = favoriteFood;
  }

  // returns true if this boa constrictor is healthy
  public boolean isHealthy(){
    return this.favoriteFood.equals("granola bars");
  }

  // returns true if the length of this boa constrictor is
  // less than the given cage length
  public boolean fitsInCage(int cageLength){
    return this.length < cageLength;
  }

  // produces the length of the Boa in inches
  public int lengthInInches(){
    return this.length * 12;
  }
}
```
And here's a new test method `testLengthInInches()` added to the `BoaTest` class:
```
public class BoaTest {
  private Boa jen;
  private Boa ken;

  @Before
  public void setUp() throws Exception {
    jen = new Boa("Jennifer", 2, "grapes");
    ken = new Boa("Kenneth", 3, "granola bars");
  }

  @Test
  public void testLengthInInches() {
    assertEquals(24, jen.lengthInInches());
    assertEquals(36, ken.lengthInInches());
  }
}
```
The `testLengthInInches()` method tests the `lengthInInches()` method of the `Boa` class by calling it on two `Boa` objects (`jen` and `ken`)
created in the `setUp()` method and verifying that the returned values are correct using the `assertEquals()` method.
The `@Test` annotation indicates that this method should be run as a JUnit test.

After running the tests, the JUnit pane should display a green bar indicating that all tests have passed.
