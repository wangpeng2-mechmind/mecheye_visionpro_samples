# VisionPro Samples

This documentation provides instructions on using the VisionPro samples to control a Mech-Eye 3D Laser Profiler and obtain 2D and 3D data. 

## Sample List

The following samples are provided:

* **AcquireIntensityAndRangeImagesEncoder**  
  Acquires intensity and depth data and generates intensity and range images. Use this sample if the scanning is triggered by an encoder.
* **AcquireIntensityAndRangeImagesFixedRate**  
  Acquires intensity and depth data and generates intensity and range images. Use this sample if the scanning is triggered at a fixed rate.

## Instructions

The prerequisites and detailed instructions for using the samples are provided below.

### Prerequisites

The following software products must be installed for the samples to be run successfully.

* Mech-Eye SDK: latest version
* Cognex VisionPro: version 9.8 SR1 tested

>Note: Make sure you know where the above products are installed. The installation directories are needed in the next step.

### Copy Dynamic-Link Libraries

The dynamic-link libraries of Mech-Eye SDK must be copied to the installation path of Vision Pro first.

1. Go to the installation path of Mech-Eye SDK and open the following folder: *xxx/Mech-Eye SDK-x.x.x/API/dll*

2. Copy the following 2 DLL files in the above folder:

   * **MechEyeApi.dll**
   * **MechEyeApiWrapper.dll**

3. Go to the installation path of VisionPro, open the **bin** folder, and paste the DLL files there.

4. Go to the installation path of Mech-Eye SDK and open the following folder: *xxx/Mech-Eye SDK-x.x.x/API/dll/net48*

5. Copy the following DLL file in the above folder:

   * **MechEyeApiNet.dll**

6. Go to the installation path of VisionPro, open the **bin** folder, and paste the DLL file there.

### Configure Script Reference

After copying the dynamic-link libraries, the path of the reference in the script must be configured for the script to run successfully.

1. Open VisionPro QuickBuild, select the **File** menu, and then select **Open QuickBuild Application**.

2. In the pop-up window, select the VisionPro sample to be used, and click the **Open** button.

3. A window with the following message will pop up. Click the **No** button to close this window.

   >**Would you like to save the current QuickBuild application?**

4. A window with the following message may pop up. If it pops up, click the **Confirm** button to close this window.

   >**Unable to load script code in Mech-Mind Image Grabber.**
   >
   >**The script will not be used until the error is corrected.**

5. Double-click **Mech-Eye 3D Laser Profiler** to open it in Job Editor.

   ![vp-3](https://docs.mech-mind.net/download/github/vp/vp-3.png)

6. In the left panel of the **Job Editor** window, double-click **Mech-Mind Image Grabber** to open the block.

   ![vp-4](https://docs.mech-mind.net/download/github/vp/vp-4.png)

7. In the pop-up **Mech-Mind Image Grabber** window, click the **Create/Edit Script** ![button](https://docs.mech-mind.net/download/github/vp/create-edit-script.png) to open Script Editor.

8. In the pop-up **Mech-Mind Image Grabber Script** window, click the **Add/Remove Reference** ![button](https://docs.mech-mind.net/download/github/vp/add-remove-reference.png) to edit the references.

9. In the pop-up **Add/Remove Referenced Assemblies** window, scroll down to the bottom and double-click **MechEyeApiNet.dll** to edit its path.

10. In the pop-up window, click the **Browse...** button, go to the installation path of Mech-Eye SDK (*xxx/Mech-Eye SDK-x.x.x/API/dll/net48*), and select the **MechEyeApiNet.dll** file.

11. Click the **OK** button to close the above window. Click the **OK** button in the **Add/Remove Referenced Assemblies** window to close this window as well.

### Set Device IP Address in Script

Before running the script, change the IP address in the script so the laser profiler can be successfully connected.

1. In the **Mech-Mind Image Grabber Script** window, locate the following line, and change the IP address in this line to the actual IP address of the laser profiler to be connected.

   ```csharp
   status = profiler.Connect("192.168.20.15", 10000);
   ```

2. Click the **Build** ![button](https://docs.mech-mind.net/download/github/vp/build.png) to save the changes.

3. Close the **Mech-Mind Image Grabber Script** and **Mech-Mind Image** windows to return to the Job Editor window.

### Obtain Intensity and Range Images

Now you can run the sample to obtain intensity and range images.

1. Click the **Run Job Once** ![button](https://docs.mech-mind.net/download/github/vp/run-job-once.png) in the upper left to run the job.

2. Check the obtained images: In the left panel, double-click on the corresponding tool to check the intensity or range image.

   * Intensity image: Double-click **CogAffineTransformTool1**.
   * Range image: Double-click **Cog3DVisionDataRerenderTool1**.

3. If the obtained images do not meet your requirements, refer to the next section for instructions on adjusting the parameters of the laser profiler.

### Adjust Laser Profiler Parameters

Parameters of the laser profiler can be adjusted in two ways: in Mech-Eye Viewer or in the script. Mech-Eye Viewer is recommended, as it provides a graphical interface and allows you to acquire the images immediately after adjusting the parameters to check the result.

>Note:
>
>You can also view the current parameter values in Mech-Eye Viewer.

#### Adjust Parameters with Mech-Eye Viewer

The [user manual](https://docs.mech-mind.net/en/eye-3d-profiler/latest/viewer/parameter-reference.html) provides detailed instructions on adjusting the parameters with Mech-Eye Viewer.

#### Adjust Parameters with the Script

The script in the VisionPro sample calls the C# Mech-Eye API to control the laser profiler. To adjust the parameters with the script, you need to modify the existing methods or add more methods for parameter adjustment.

The names of the methods for parameter adjustments follow this pattern: `SetXxxValue()`, where `Xxx` is a data type.

[Mech-Eye API Reference](https://docs.mech-mind.net/en/eye-3d-profiler/latest/api/api-reference.html) provides explanations of parameter data types and the methods for parameter adjustments.
