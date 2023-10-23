# selenium-methods

# Syntax for WebDriver Methods

# Creating New Instance Of Firefox Driver – this will open an new Empty browser
WebDriver driver = new FirefoxDriver();

# Command To Open URL In Browser
driver.get(“http://selenium-suresh.blogspot.com”);
This syntax will open specified URL of software web application in web browser.

# Clicking on any element or button of webpage
driver.findElement(By.id(“id of any element or button”)).click();

# Store text of targeted element in variable – This will retrieve text from targeted element of software web application page and will store it in variable = suresh
String suresh = driver.findElement(By.tagName(“select”)).getText();

# Typing text in text box or text area.
driver.findElement(By.name(“txtboxname”)).sendKeys(“My First Name”);

# Applying Implicit wait in webdriver – This syntax will force webdriver to wait for 15 second if element not found on page of software web application.
driver.manage().timeouts().implicitlyWait(15, TimeUnit.SECONDS);

# Applying Explicit wait in webdriver – This will wait for till 15 seconds for expected text “Time left: 7 seconds” to be appear on targeted element.
WebDriverWait wait = new WebDriverWait(driver, 15);
wait.until(ExpectedConditions.textToBePresentInElementLocated(By.xpath(“xpathofelement”), “Time left: 7 seconds”));

# Get page title in selenium webdriver
driver.getTitle();

# Get Current Page URL In Selenium WebDriver- It will retrieve current page URL and you can use it to compare with your expected URL.
driver.getCurrentUrl();

# Get domain name using java script executor – This will retrieve your software application’s domain name using webdriver’s java script executor interface and store it in to variable.
JavascriptExecutor javascript = (JavascriptExecutor) driver;
String CurrentURLUsingJS=(String)javascript.executeScript(“return document.domain”);

# Generate alert using webdriver’s java script executor interface — It will generate alert during your selenium webdriver test case execution.
JavascriptExecutor javascript = (JavascriptExecutor) driver;
javascript.executeScript(“alert(‘Test Case Execution Is started Now..’);”);

# Selecting or Deselecting value from drop down in selenium webdriver.
- Select By Visible Text– It will select value from drop down list using visible text
value = “Audi”.
Select mydrpdwn = new Select(driver.findElement(By.id(“Carlist”)));
mydrpdwn.selectByVisibleText(“Audi”);

- Select By Value- It will select value by value = “Italy”.
Select listbox = new Select(driver.findElement(By.xpath(“//select[@name=’FromLB’]”)));
listbox.selectByValue(“Italy”);

- Select By Index- It will select value by index= 0(First option).
Select listbox = new Select(driver.findElement(By.xpath(“//select[@name=’FromLB’]”)));
listbox.selectByIndex(0);

- Deselect by Visible Text- It will deselect option by visible text = Russia from list box.
Select listbox = new Select(driver.findElement(By.xpath(“//select[@name=’FromLB’]”)));
listbox.deselectByVisibleText(“Russia”);

- Deselect by Value- It will deselect option by value = Mexico from list box.
Select listbox = new Select(driver.findElement(By.xpath(“//select[@name=’FromLB’]”)));
listbox.deselectByValue(“Mexico”);

- Deselect by Index- It will deselect option by value = Mexico from list box.
Select listbox = new Select(driver.findElement(By.xpath(“//select[@name=’FromLB’]”)));
listbox.deselectByIndex(5);
It will deselect option by Index = 5 from list box.

- Deselect All – It will remove all selections from list box of software application’s page.
Select listbox = new Select(driver.findElement(By.xpath(“//select[@name=’FromLB’]”)));
listbox.deselectAll();

isMultiple()-It will return true if select box is multiselect else it will return false

- Select listbox = new Select(driver.findElement(By.xpath(“//select[@name=’FromLB’]”)));
boolean value = listbox.isMultiple();


# Navigate to URL or Back or Forward in Selenium Webdriver – 1st command will navigate to specific URL, 2nd will navigate one step back and 3rd command will navigate one step forward.
driver.navigate().to(“http://selenium-suresh.blogspot.com”);
driver.navigate().back();
driver.navigate().forward();

# Verify Element Present in Selenium WebDriver — It will return true if element is present on page, else it will return false in variable iselementpresent.
Boolean iselementpresent =driver.findElements(By.xpath(“//input[@id=’text2′]”)).size()!= 0;

# Capturing entire page screenshot in Selenium WebDriver – It will capture page screenshot and store it in your D: drive.
File screenshot = ((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
FileUtils.copyFile(screenshot, new File(“D:\\screenshot.jpg”));

# Generating Mouse Hover Event In WebDriver– This will move mouse on targeted element.
Actions actions = new Actions(driver);
WebElement moveonmenu = driver.findElement(By.xpath(“//div[@id=’menu1′]/div”));
actions.moveToElement(moveonmenu).build().perform();

# Handling Multiple Windows In Selenium WebDriver.
Get All Window Handles.—This will give you to get window handle and then how to switch from one window to another window.

Set<String> AllWindowHandles = driver.getWindowHandles();
Extract parent and child window handle from all window handles.
String window1 = (String) AllWindowHandles.toArray()[0];
String window2 = (String) AllWindowHandles.toArray()[1];

# Use window handle to switch from one window to other window.
driver.switchTo().window(window2);

# Check Whether Element is Enabled Or Disabled In Selenium Web driver- This will verify that element (text box) fname is enabled or not. You can use it for any input element.
boolean fname = driver.findElement(By.xpath(“//input[@name=’fname’]”)).isEnabled(); System.out.print(fname);

# Selenium WebDriver Assertions With TestNG Framework
- assertEquals
Assert.assertEquals(actual, expected);
assertEquals assertion helps you to assert actual and expected equal values.

- assertNotEquals
Assert.assertNotEquals(actual, expected);
assertNotEquals assertion is useful to assert not equal values.

- assertTrue
Assert.assertTrue(condition);
assertTrue assertion works for boolean value true assertion.

- assertFalse
Assert.assertFalse(condition);
assertFalse assertion works for boolean value false assertion.

# Submit() method to submit form 
driver.findElement(By.xpath(“//input[@name=’Company’]”)).submit(); 
It will submit the form.

# Handling Alert, Confirmation and Prompts Popups
String myalert = driver.switchTo().alert().getText(); To store alert text.
driver.switchTo().alert().accept(); To accept alert.
driver.switchTo().alert().dismiss(); To dismiss confirmation.
driver.switchTo().alert().sendKeys(“This Is John”); To type text In text box of prompt popup.

# Handling DRAG and DROP
WebDriver d = new FirefoxDriver();
Actions a=new Actions(d);
a.dragAndDrop(d.findElement(By.id(“draggable”)),d.findElement(By.id(“droppable”))).
build().perform;

# Handling the frames in Webdriver
- To Enter/Select the Frame  
driver.switchTo().frame(“frameid/name / index”)

# To Exit from Frame – driver.switchTo().defaultContent()
CALENDAR popups –/*IRCTC calendar*/
driver.findElement(By.id(“calendar_icon1”)).click(); driver.findElement(By.xpath(“//div[@id=’CalendarControl’]/table[tbody[tr[td[text()=’October 2012′]]]]/descendant::a[text()=’5′]”)).click();

# Context Click (Right Click)
WebElement parentMenu = driver.findElement(By.linkText(“Tourist Trains”)); Actions act = new Actions(driver); //Create Action object for Driver act.contextClick(parentMenu).build().perform(); //Context Click act.sendKeys(Keys.ARROW_RIGHT).build().perform(); Thread.sleep(1000); act.sendKeys(Keys.ARROW_DOWN).build().perform(); Thread.sleep(1000); act.sendKeys(Keys.ENTER).build().perform();

# Other Browser (Internet Explorer)
System.setProperty(“webdriver.ie.driver”,”D:l\\browserdrivers\\IEDriverServer.exe”); WebDriver driver =new InternetExplorerDriver();
driver.get(“http://www.google.com”);

# Other Browser (Chrome)
System.setProperty(“webdriver.chrome.driver”,”D:\\browserdrivers\\Chromedriver.exe”); WebDriver driver = new ChromeDriver();
driver.get(“http://www.google.com”);


# Using Auto-IT tool -To handle windows authentication and calling that code in Selenium
- Auto-IT code
WinWaitActive(“Authentication Required”)
Send(“admin”)
Send(“{TAB} admin{TAB} {ENTER}”)
Save the file as default save.(Authentication1.exe)

- Calling AutoIT .exe file in selenium
Process P = Runtime.getRuntime().exec(“D:\\AUTOIT\\Authentication1.exe”);

# File download using RobotClass
Robot robot = new Robot();
//it clicks on SaveFile Radio btn
robot.keyPress(KeyEvent.VK_ALT);
robot.keyPress(KeyEvent.VK_S);
robot.keyRelease(KeyEvent.VK_ALT);
robot.keyRelease(KeyEvent.VK_S);
Thread.sleep(2000);
//Clicks on OK btn
robot.keyPress(KeyEvent.VK_ENTER);
robot.keyRelease(KeyEvent.VK_ENTER);
Thread.sleep(2000);
System.out.println(“File downloaded successfully”);

# File Uplad using WebDriver
WebElement fileInput = driver.findElement(By.xpath(“//input[@type=’file’][@name=’photofile’]”));
fileInput.sendKeys(“C:\\Users\\Public\\Pictures\\Sample Pictures\\Desert.jpg”);
Thread.sleep(5000);
System.out.println(“File uploaded successfully”);

