# Test Case: Tutorial 7 - Delete Multiple Created Assets  

## Objective  

The objective of this test is to delete multiple **Test MiX New Assets** from the system.  

## Steps  

1. **Login** to [UAT.mixtelematics.com](https://uat.mixtelematics.com) with the following credentials:  
   - **Username:** `shakedown.fleet@mailinator.com`  
   - **Password:** `shakedownfleet123`

2. **Select Organisation:**  
   - Navigate to **Test RSO** > **MiX Automation**  

3. **Navigate to Assets:**  
   - Click on the **Monitor** tab  
   - Click on **Assets**  

4. **Filter and Delete Assets:**  
   - Filter Assets by entering **"Test MiX New Asset"** in the filter bar  
   - Retrieve the number of assets displayed after filtering  
   - Output the total number of assets to delete:  

 ```java
     System.out.println("Number of Assets to delete: " + count);
 ```  

- Create a loop to delete all **Test MiX New Assets**  
  - Select the first asset  
  - Click **Remove**  
  - Confirm removal  
  - Repeat until all assets are deleted  

## Notes  

- Ensure that the loop continues until the number of filtered assets reaches **0**.  
- The asset count should be retrieved from the top-left filter results.  
- Verify that all **Test MiX New Assets** are successfully removed.  
