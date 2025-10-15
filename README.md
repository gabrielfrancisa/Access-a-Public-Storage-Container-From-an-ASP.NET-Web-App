# Access-a-Public-Storage-Container-From-an-ASP.NET-Web-App
I designed and achieved the following: Added Azure Storage capabilities to an ASP.NET MVC project. Accessed an Azure Storage account programmatically. Provisioned an Azure Storage blob container that has public access. Uploaded files to an Azure Storage blob container. Retrieved a list of files from an Azure Storage blob container


## 1. Configure the project in Visual Studio.
Open Microsoft Edge, and then sign in to the Azure portal as user
If prompted to Stay signed in, select Yes.

A cloud slice is a subset of an Azure subscription that has been assigned to a user account that was provisioned for you for the duration of this Challenge Lab. A cloud slice provides temporary access to a subset of resources available in a cloud subscription so that you can learn the concepts in this Challenge Lab without having to configure your own subscription.

A cloud slice has restrictions on the types of administrative activities that are allowed. Please follow the instructions carefully, especially with regard to names and other configuration details.


Enable Allow Blob anonymous access in the salod55547061 storage account.
Expand this hint for guidance on enabling Blob anonymous access in a storage account.
Copy the Key value and Connection string for key1 in the salod55547061 storage account, and then record the values in the following text boxes:

key1 Key (no leading or trailing spaces)

key1 Connection String (no leading or trailing spaces)

Expand this hint for guidance on copying the connection string for the storage account.
Open the D:\challenge\AzureStorageDevelopment.sln solution in Microsoft Visual Studio 2019, and then sign in to Visual Studio as CS-55547061@cloudslice.onmicrosoft.com by using epY&&n9R as the password.
Expand this hint for guidance on opening the solution in Visual Studio 2019.
After signing in, you may have to select Check for an updated license.

It may take several minutes for Visual Studio to load for the first time.

The ASP.NET MVC project for this challenge is in the D:\challenge folder. The file CSSD01.txt in D:\challenge\StorageChallenge contains a list of the files and objects used for this challenge. You will write all of the code for this challenge in a single code file.

Add the Azure.Storage.Blobs NuGet Package to the StorageChallenge project.
Expand this hint for guidance on adding the Azure.Storage.Blobs NuGet Package.
You may need to enlarge the NuGet Package Manager window to see the Install option.

You can ignore any prompts regarding missing NuGet packages.

Open the Web.config file, set the TestType appSetting value to 1, set the StorageAccountConnectionString appSetting value to <storageAccountConnectionString> and then Save Web.config.
Expand this hint for guidance on configuring the testType appSetting.
Leave the project open for the rest of the challenge.

## 2. Implement the UploadFile method.
In Solution Explorer, open Models/StorageContext.cs.
Expand this hint for guidance on locating the StorageContext.cs file.
Add a private string field named connectionString to the StorageContext class.
Expand this hint for guidance on adding a private string field.
Implement the StorageContext constructor by assigning the connectionString parameter to the connectionString field.
Expand this hint for guidance on implementing the constructor.
The constructor for a class in C# is a method that has no name and has a return type that matches the class.

Import the System.IO namespace and the Azure.Storage.Blobs namespace into the StorageContext.cs file.
Expand this hint for guidance on importing namespaces.
In the UploadFile method, create an instance of the BlobContainerClient class by using the connectionString field and the containerName parameter, and then assign the instance to a variable named container.
Expand this hint for guidance on creating the container variable.
The data structure of the BlobFileData is documented at the beginning of the StorageContext.cs file.

In the UploadFile method, create the container if it does not already exist, and then configure it to allow public blob access by using the SetAccessPolicy method.
Expand this hint for guidance on creating the container.
In the UploadFile method, upload the file referenced by the fileData parameter to the container by using the UploadBlob method.
Expand this hint for guidance on uploading a file to the container.
Save the StorageContext.cs file and leave it open for the next task.

## 3.Implement the GetFileList method.
In the StorageContext.cs file, in the GetFileList method, create an instance of the List <BlobFileData> class, and then assign the instance to a variable named results.
Expand this hint for guidance on creating the results variable.
In the GetFileList method, create an instance of the BlobContainerClient class by using the connectionString field and the containerName parameter, and then assign the instance to a new variable named container.
Expand this hint for guidance on adding the container variable.
In the GetFileList method, create a string variable named sas to store a shared access signature (SAS) by using the values in the following table:

Item	Description
Parameter to evaluate	isPrivate
Value if true	The return value of the GetSAS(containerName) method
Value if false	An empty string
Expand this hint for guidance on creating the sas variable.
In this challenge, the isPrivate parameter will always be false, so you do not need to implement the GetSAS method yet.

In the GetFileList method, retrieve the blobClient object from the container by passing the blob name to the GetBlobClient method, assign the properties in the following table, and then return the list of BlobFileData objects.

Property	Value
Name	blobClient.Name
URL	blobClient.Uri.AbsoluteUri
SAS	sas
Expand this hint for guidance on generating a list of BlobFileData objects.
Save the StorageContext.cs file.
The BlobFileData data structure is documented at the beginning of the StorageContext.cs file.

Blob files are accessed by using the Azure Storage REST API. 
Displaying the files by using their URI takes advantage of the nature of REST APIs.

## 4.Test the application
Run the application, enter the connection string <storageAccountConnectionString> in the Storage Account Connection String textbox, select Test, and then review the results.
Expand this hint for guidance on testing the application.
If may take a couple minutes for the Storage Challenge test page to appear.

The following screenshot shows the expected results:The output of the test

If you repeat the test after success, the Public Blob Upload will fail as the files already exist, but the Public Blob Download will succeed again.

5. Summary
Congratulations, 
