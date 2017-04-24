## Unit Testing
* Unit Test Project in Visual Studio
* Can be added to a Visual Studio Solution as another project
* Test Menu >> Run Tests
* Microsoft.VisualStudio.TestTools.UnitTesting namespace
* C# Attributes with square brackets
  * [TestClass] - Class that has Tests in it (must be public)
  * [TestMethod] - Method of a test class to be executed
* **Assert** Class that will make assertions about the test
  * Assert.AreEqual(3, 4); => Error
* Hard to Assert against Floating Point Numbers
  * floats and doubles have a **delta** that will check if a float/double is close enough.