# Test Case: Tutorial 8 - Get the Current Date and Time  

## Objective  

The objective of this test is to write the **current date and time** as the **Passenger Name** and perform subsequent actions.  

## Steps  

1. **Login** to [uat.mixtelematics.com](https://uat.mixtelematics.com) with the following credentials:  
   - **Username:** `shakedown.fleet@mailinator.com`  
   - **Password:** `shakedownfleet123`

2. **Select Organisation:**  
   - Navigate to **Test RSO** > **MiX Automation**  

3. **Navigate to Passengers:**  
   - Click on the **Monitor** tab  
   - Click on **Passengers**  

4. **Add a New Passenger:**  
   - Click the **Green +** sign (**Add Passenger**)  
   - Under **Passenger Name**, write the **current date and time**.  
     - This can be done dynamically using a function to get the current date and time, such as:  

   ```java
       String currentDateTime = java.time.LocalDateTime.now().toString();
       passengerNameField.sendKeys(currentDateTime);
   ```

   - Click **Save**  

5. **Filter for the Created Passenger:**  
   - Use the filter to find the newly created passenger by their **Name** (the current date and time).  

6. **Remove the Created Passenger:**  
   - Select the passenger  
   - Click **Remove**  
   - Confirm the removal  

## Notes  

- Ensure that the **current date and time** is accurately captured and displayed in the passenger name.  
- Verify that the newly created passenger appears in the list after saving.  
- Confirm that the passenger is successfully removed.  
