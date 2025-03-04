# Test Case: Tutorial 5 - Write Using Robot  

## Objective  
The objective of this test is to add an asset and write the **Registration Number** using Robot.  

## Steps  

1. **Login** to [uat.mixtelematics.com](https://uat.mixtelematics.com) with the following credentials:  
   - **Username:** `shakedown.fleet@mailinator.com`  
   - **Password:** `shakedownfleet123`

2. **Select Organisation:**  
   - Navigate to **Test RSO** > **MiX Automation**  

3. **Navigate to Assets:**  
   - Click on the **Monitor** tab  
   - Click on **Assets**  

4. **Add a New Asset:**  
   - Click the **Green +** sign (**Add Asset**)  
   - Enter **Asset Description**: `"Test New MiX Asset"`  
   - Select **Asset Type**: `"Light Vehicle"`  
   - Enter **Registration Number** using Robot: `"9876543210"`  
   - Select **Site**: `"Default Site"`  
   - Click **Save**  
   - Click **Close**  

5. **Remove the Asset:**  
   - Filter for the newly created asset  
   - Remove the asset  
   - Confirm removal  

## Notes  
- Ensure that the **Registration Number** is entered correctly using Robot.  
- Verify that the asset appears in the list before removal.  
- Confirm that the asset is successfully removed.  
- When testing, you may need to check **timing** to ensure smooth execution.  
