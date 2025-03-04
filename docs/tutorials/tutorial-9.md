# Test Case: Tutorial 9 - Work with Multiple Environments  

## Objective  
The objective of this test is to learn how to work with **multiple environments** (UAT and INT) and extract **Last Trip Details** based on the environment.  

## Steps  

1. **Login** to [uat.mixtelematics.com](https://uat.mixtelematics.com) with the following credentials:  
   - **Username:** `shakedown.fleet@mailinator.com`  
   - **Password:** `shakedownfleet123`

2. **Select Organisation:**  
   - Navigate to **Test RSO** > **MiX Automation**  

3. **Navigate to Assets:**  
   - Click on the **Monitor** tab  
   - Click on **Assets**  

4. **Filter for 'MiX Automation Live Unit':**  
   - Use the filter to find the **'MiX Automation Live Unit'** asset  

5. **Extract the Last Trip Details:**  
   - Write a function that checks the current environment and retrieves the **Last Trip Details** accordingly.  
   - The function should differentiate between UAT and INT environments:  

   **HINT:**  
   ```  
   if (currentEnvironment == Enums.Environment.INT) {  
       // Logic for extracting details in INT environment  
   } else {  
       // Logic for extracting details in UAT environment  
   }  
   ```

## Notes  
- The XPath used to extract **Last Trip Details** in UAT and INT environments will differ.  
- Use an enum (`Enums.Environment.UAT` or `Enums.Environment.INT`) to manage the environment-based extraction.  
- Verify that the correct details are retrieved for both environments.  