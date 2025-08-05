***AI Generated***

Roo Prompt: Create a file documenting all the models and what they are used for.  Basically a text version of the mermaid diagram with additional details

# CAHPS Models Documentation

This document provides a detailed description of the data models used in the CAHPS application.

## Client

Represents a client entity in the system.

**Properties:**

- `Id` (string): The unique identifier for the client.
- `ParentClientId` (string): The identifier of the parent client, if any.
- `ParentClient` (Client): Navigation property to the parent client.
- `ChildClients` (IEnumerable<Client>): Navigation property to child clients.
- `ClientName` (string): The name of the client.
- `ClientProgramTypeId` (int): The program type identifier for the client.
- `CCN` (string): The client's CCN.
- `NPI` (string): The client's NPI.
- `StateId` (string): The state identifier for the client.
- `UserClients` (List<UserClient>): Navigation property to the associated user-client relationships.
- `CahpsClientOption` (CahpsClientOption): Navigation property to the client's CAHPS options.
- `ClientSurveys` (List<ClientSurvey>): Navigation property to the client's surveys.

---

## Batch

Represents a batch of surveys to be sent to a subcontractor.

**Properties:**

- `Id` (string): The unique identifier for the batch.
- `SampleMonth` (SampleMonth): Navigation property to the sample month.
- `SampleMonthId` (string): The identifier of the sample month.
- `BatchType` (BatchType): The type of the batch.
- `Wave` (int): The wave number of the batch.
- `Round` (int): The round number of the batch.
- `IsException` (bool): Indicates if the batch is an exception.
- `CreatedOn` (DateTime): The date the scheduled batch record was created.
- `BatchScheduledDate` (DateTime): The scheduled date for the batch.
- `BatchStartedDate` (DateTime?): The date the batch started the process of generating and sending.
- `BatchSentDate` (DateTime?): The date the batch was sent to the subcontractor.
- `CollectionBeganDate` (DateOnly): The date that data collection will begin.
- `BatchFileName` (string): The file name of the batch in Cloud Storage.
- `BatchFilePath` (string): The file path of the batch in Cloud Storage.
- `SurveyCount` (int?): The number of surveys in the batch.
- `SeedCount` (int?): The number of seeds in the batch.
- `ProviderCount` (int?): The number of providers in the batch.
- `Status` (BatchStatus): The status of the batch.

---

## BatchSample

Represents a sample included in a batch.

**Properties:**

- `Id` (int): The unique identifier for the batch sample.
- `Batch` (Batch): Navigation property to the batch.
- `BatchId` (string): The identifier of the batch.
- `Sample` (Sample?): Navigation property to the sample. Will be null for seeds.
- `SampleId` (int?): The identifier of the sample.
- `SeedClient` (Client?): Navigation property to the client for seeds. Will be null for samples.
- `SeedClientId` (string?): The identifier of the seed client.
- `Barcode` (string): The barcode text for the survey.

---

## CahpsClientFileDefinition

Represents the file definition for a CAHPS client.

**Properties:**

- `CahpsClientOptionId` (int): The identifier of the CAHPS client option.
- `CahpsClientOption` (CahpsClientOption): Navigation property to the CAHPS client option.
- `FileDefinitionId` (int): The identifier of the file definition.
- `FileDefinition` (FileDefinition): Navigation property to the file definition.

---

## CahpsClientLanguage

Represents the language for a CAHPS client.

**Properties:**

- `CahpsClientOptionId` (int): The identifier of the CAHPS client option.
- `CahpsClientOption` (CahpsClientOption): Navigation property to the CAHPS client option.
- `CahpsLanguageId` (int): The identifier of the CAHPS language.
- `CahpsLanguage` (CahpsServiceLanguage): Navigation property to the CAHPS service language.

---

## CahpsClientOption

Represents the CAHPS options for a client.

**Properties:**

- `Id` (int): The unique identifier for the CAHPS client option.
- `ClientId` (string): The identifier of the client.
- `Client` (Client): Navigation property to the client.
- `StartDate` (DateTime?): The start date of the option.
- `EndDate` (DateTime?): The end date of the option.
- `AutoRenew` (bool): Indicates if the option auto-renews.
- `RenewalTerm` (CahpsRenewalTerm): The renewal term for the option.
- `RenewalCycle` (int): The renewal cycle for the option.
- `SurveyMode` (CahpsSurveyMode): The survey mode.
- `StartSampleMonth` (DateTime): The start sample month.
- `EndSampleMonth` (DateTime?): The end sample month.
- `SamplingMethod` (CahpsSamplingMethod): The sampling method.
- `TargetCompletions` (int): The target number of completions.
- `AnnualCensus` (int): The annual census.
- `CAHPSFileDefinitions` (List<CahpsClientFileDefinition>): Navigation property to the CAHPS file definitions.
- `SoftwareVendor` (string?): The software vendor.
- `PrimaryLanguageId` (int?): The identifier of the primary language.
- `PrimaryLanguage` (CahpsServiceLanguage?): Navigation property to the primary language.
- `EnableCahpsLanguages` (List<CahpsClientLanguage>): Navigation property to the enabled CAHPS languages.
- `CMSExempt` (bool): Indicates if the client is CMS exempt.
- `Comments` (string?): Comments about the client option.
- `TemporarilyDisabled` (bool): Indicates if the client option is temporarily disabled.
- `MonthlyServiceFee` (decimal?): The monthly service fee.
- `LogoFileName` (string?): The filename of the logo.
- `LogoUploadId` (string?): The upload identifier of the logo.
- `AgencyNameForSurvey` (string?): The agency name for the survey.
- `CECSParticipant` (bool): Indicates if the client is a CECS participant.
- `CreatedOn` (DateTime?): The date the option was created.
- `CreatedByUserId` (string?): The identifier of the user who created the option.
- `ModifiedOn` (DateTime?): The date the option was modified.
- `ModifiedByUserId` (string?): The identifier of the user who modified the option.
- `CahpsCID` (string?): The CAHPS CID.

---

## CahpsService

Represents a CAHPS service.

**Properties:**

- `Id` (int): The unique identifier for the CAHPS service.
- `Name` (string): The name of the CAHPS service.
- `FileDefinitions` (ICollection<FileDefinition>): Navigation property to the file definitions.
- `FileTypes` (ICollection<FileType>): Navigation property to the file types.

---

## CahpsServiceLanguage

Represents a language for a CAHPS service.

**Properties:**

- `Id` (int): The unique identifier for the CAHPS service language.
- `Description` (string): The description of the language.
- `ProgramTypeId` (int): The program type identifier.
- `ProgramType` (CahpsService): Navigation property to the CAHPS service.
- `LanguageCode` (string): The language code.

---

## CahpsUserOptions

Represents the CAHPS options for a user.

**Properties:**

- `Id` (int): The unique identifier for the user options.
- `User` (User): Navigation property to the user.
- `UserId` (string): The identifier of the user.
- `FileDefinition` (FileDefinition?): Navigation property to the file definition.
- `FileDefinitionId` (int?): The identifier of the file definition.
- `FolderName` (string?): The folder name.

---

## CallDataImport

Represents a call data import.

**Properties:**

- `Id` (string): The unique identifier for the call data import.
- `FileName` (string): The name of the imported file.
- `TotalRows` (int): The total number of rows in the file.
- `SuccessRows` (int): The number of successfully imported rows.
- `WarningRows` (int): The number of rows with warnings.
- `FailureRows` (int): The number of rows that failed to import.
- `StorageKey` (string): The storage key for the imported file.
- `ImportDate` (DateTime): The date of the import.
- `RawCallDataRecords` (ICollection<RawCallData>): Navigation property to the raw call data records.

---

## ClientApp

Represents the CAHPS service term for a client.

**Properties:**

- `Id` (int): The unique identifier for the client application.
- `ClientId` (string?): The identifier of the client.
- `Client` (Client?): Navigation property to the client.
- `AppId` (int): The application identifier.
- `StartDate` (DateTime?): The start date of the application.
- `EndDate` (DateTime?): The end date of the application.
- `SuspendedAt` (DateTime?): The date the application was suspended.
- `SuspendedById` (string?): The identifier of the user who suspended the application.
- `DeletedAt` (DateTime?): The date the application was deleted.
- `DeletedById` (string?): The identifier of the user who deleted the application.
- `SuspendReason` (int): The reason for suspension.
- `SuspendNote` (string?): A note about the suspension.

---

## ClientSurvey

A released survey version for a client.

**Properties:**

- `Id` (string): The unique identifier for the client survey.
- `ClientSurveyCode` (string): Text identifier for the agency's survey version.
- `Name` (string): Display name of the client to print on the survey.
- `Client` (Client): Navigation property to the client.
- `ClientId` (string): The identifier of the client.
- `Survey` (Survey): Navigation property to the survey.
- `SurveyId` (string): The identifier of the survey.
- `CreatedDate` (DateTime): The date the survey was created.
- `CreatedBy` (User): Navigation property to the user who created the survey.
- `CreatedById` (string): The identifier of the user who created the survey.
- `ModifiedDate` (DateTime?): The date the survey was modified.
- `ModifiedBy` (User?): Navigation property to the user who modified the survey.
- `ModifiedById` (string?): The identifier of the user who modified the survey.
- `DeletedDate` (DateTime?): The date the survey was deleted.
- `DeletedBy` (User?): Navigation property to the user who deleted the survey.
- `DeletedById` (string?): The identifier of the user who deleted the survey.
- `StartDate` (DateOnly): The start date of the survey.
- `EndDate` (DateOnly?): The end date of the survey.
- `Language` (CahpsServiceLanguage): Navigation property to the language of the survey.
- `LanguageId` (int): The identifier of the language of the survey.

---

## DataCollection

Represents a data collection period.

**Properties:**

- `Id` (string): The unique identifier for the data collection.
- `Year` (int): The year of the data collection.
- `Month` (int): The month of the data collection.
- `SampleMonth` (SampleMonth): Navigation property to the sample month.
- `SampleMonthId` (string): The identifier of the sample month.
- `MonthYear` (DateOnly): The month and year of the data collection.
- `Client` (Client): Navigation property to the client.
- `ClientId` (string): The identifier of the client.
- `CollectionStatus` (DataCollectionStatus): The status of the data collection.
- `WaveOneDataCollectionStartDate` (DateOnly): Date that Wave 1 should start collecting data.
- `WaveTwoDataCollectionStartDate` (DateOnly): Date that Wave 2 should start collecting data.
- `DataCollectionEndDate` (DateOnly): Date that we will no longer accept data.
- `SampledDate` (DateOnly?): Date that samples were created for this record.
- `WaveOneBatchedDate` (DateOnly?): Date that Wave 1 batch was created and sent to subcontractors.
- `WaveTwoBatchedDate` (DateOnly?): Date that Wave 2 batch was created and sent to subcontractors.
- `WaveOneBatch` (Batch?): Navigation property to the Wave 1 batch.
- `WaveOneBatchID` (string?): The identifier of the Wave 1 batch.
- `WaveTwoBatch` (Batch?): Navigation property to the Wave 2 batch.
- `WaveTwoBatchID` (string?): The identifier of the Wave 2 batch.
- `RandomSeed` (int?): The random seed for the data collection.
- `CMSApprovedLate` (bool): Indicates if the data collection was approved late by CMS.
- `MonthlyTarget` (int): The monthly target for the data collection.
- `LogoFileName` (string?): The filename of the logo.
- `LogoUploadId` (string?): The upload identifier of the logo.
- `SurveyMode` (CahpsSurveyMode): The survey mode.
- `SamplingMethod` (CahpsSamplingMethod): The sampling method.
- `TargetCompletions` (int): The target number of completions.
- `AgencyNameForSurvey` (string?): The agency name for the survey.
- `IsOnHold` (bool): Indicates if the data collection is on hold.
- `Samples` (ICollection<Sample>): Navigation property to the samples.

---

## DataManagerFileUpload

Represents a file upload in the data manager.

**Properties:**

- `Id` (string): The unique identifier for the file upload.
- `FieldType` (DataManagerFieldType): The field type of the file upload.
- `Filename` (string): The filename of the uploaded file.
- `UploadDate` (DateTime): The date of the upload.
- `UploadedById` (string): The identifier of the user who uploaded the file.
- `UploadedBy` (User): Navigation property to the user who uploaded the file.

---

## FileDefinition

Represents a file definition.

**Properties:**

- `Id` (int): The unique identifier for the file definition.
- `Name` (string): The name of the file definition.
- `CahpsServiceId` (int): The identifier of the CAHPS service.
- `CahpsService` (CahpsService): Navigation property to the CAHPS service.

---

## FileType

Represents a file type.

**Properties:**

- `Id` (int): The unique identifier for the file type.
- `Name` (string): The name of the file type.
- `CahpsServiceId` (int): The identifier of the CAHPS service.
- `CahpsService` (CahpsService): Navigation property to the CAHPS service.

---

## FileUpload

Represents a file upload.

**Properties:**

- `Id` (string): The unique identifier for the file upload.
- `FileName` (string): The name of the uploaded file.
- `FileSize` (long): The size of the uploaded file.
- `MimeType` (string): The MIME type of the uploaded file.
- `TotalRecords` (int): The total number of records in the file.
- `EligibleRecords` (int): The number of eligible records in the file.
- `UploadStatus` (UploadStatusEnum): The status of the upload.
- `UploadedById` (string): The identifier of the user who uploaded the file.
- `UploadedBy` (User): Navigation property to the user who uploaded the file.
- `UploadDate` (DateTime): The date of the upload.
- `FileDefinitionId` (int): The identifier of the file definition.
- `FileDefinition` (FileDefinition): Navigation property to the file definition.
- `IsTestFile` (bool): Indicates if the file is a test file.

---

## FileUploadLog

Represents a log for a file upload.

**Properties:**

- `Id` (int): The unique identifier for the log.
- `ModelId` (string): The identifier of the model.
- `ModelType` (string): The type of the model.
- `LogType` (LogType): The type of the log.
- `FieldName` (string?): The name of the field.
- `RowNumber` (int): The row number.
- `Message` (string): The log message.

---

## FileUploadRawDataHospice

Represents raw data from a hospice file upload.

**Properties:**

- `Id` (int): The unique identifier for the raw data.
- `FileUploadId` (string): The identifier of the file upload.
- `FileUpload` (FileUpload): Navigation property to the file upload.
- `RowNumber` (int): The row number.
- `ProviderName` (string?): The name of the provider.
- `ProviderId` (string?): The identifier of the provider.
- `NPI` (string?): The NPI of the provider.
- `TotalDecedentCount` (int): The total number of decedents.
- `LiveDischargeCount` (int): The number of live discharges.
- `NoPublicityCount` (int): The number of no publicity requests.
- `SampleMonth` (DateOnly): The sample month.
- `ProviderDecedentId` (string?): The provider's identifier for the decedent.
- `DecedentPrefix` (string?): The prefix of the decedent's name.
- `DecedentFirstName` (string?): The first name of the decedent.
- `DecedentMiddleInitial` (string?): The middle initial of the decedent.
- `DecedentLastName` (string?): The last name of the decedent.
- `DecedentSuffix` (string?): The suffix of the decedent's name.
- `BirthDate` (DateOnly): The birth date of the decedent.
- `DeathDate` (DateOnly): The death date of the decedent.
- `AdmissionDate` (DateOnly): The admission date of the decedent.
- `Gender` (string?): The gender of the decedent.
- `Race` (IEnumerable<string>): The race of the decedent.
- `Hispanic` (string?): Indicates if the decedent is Hispanic.
- `PrimaryDiagnosis` (string?): The primary diagnosis of the decedent.
- `LastCareLocation` (string?): The last care location of the decedent.
- `PrimaryPayer` (string?): The primary payer of the decedent.
- `SecondaryPayer` (string?): The secondary payer of the decedent.
- `OtherPayer` (string?): The other payer of the decedent.
- `FacilityId` (string?): The identifier of the facility.
- `FacilityName` (string?): The name of the facility.
- `BranchId` (string?): The identifier of the branch.
- `BranchName` (string?): The name of the branch.
- `SurveyLanguage` (string?): The language of the survey.
- `Relationship` (string?): The relationship of the caregiver to the decedent.
- `CaregiverPrefix` (string?): The prefix of the caregiver's name.
- `CaregiverFirstName` (string?): The first name of the caregiver.
- `CaregiverMiddleInitial` (string?): The middle initial of the caregiver.
- `CaregiverLastName` (string?): The last name of the caregiver.
- `CaregiverSuffix` (string?): The suffix of the caregiver's name.
- `MailingAddress1` (string?): The first line of the mailing address.
- `MailingAddress2` (string?): The second line of the mailing address.
- `City` (string?): The city of the mailing address.
- `State` (string?): The state of the mailing address.
- `ZipCode` (string?): The zip code of the mailing address.
- `Telephone1` (string?): The first telephone number.
- `Telephone2` (string?): The second telephone number.
- `Telephone3` (string?): The third telephone number.
- `EmailAddress` (string?): The email address.
- `ProviderCustomFields` (Dictionary<string, string>): Custom fields for the provider.
- `DecedentCustomFields` (Dictionary<string, string>): Custom fields for the decedent.
- `HospiceOffices` (int): The number of hospice offices.
- `MissingAddress` (bool): Indicates if the address is missing.
- `MissingDeathDate` (bool): Indicates if the death date is missing.
- `MissingDecedent` (bool): Indicates if the decedent is missing.
- `MissingTelephone` (bool): Indicates if the telephone number is missing.
- `MissingCaregiver` (bool): Indicates if the caregiver is missing.
- `DuplicateFlag` (bool): Indicates if the record is a duplicate.
- `DuplicateOfRowNumber` (int): The row number of the duplicate record.

---

## FileUploadRecord

Represents a record in a file upload.

**Properties:**

- `Id` (int): The unique identifier for the record.
- `CMSProviderId` (string?): The CMS provider identifier.
- `FileUploadId` (string): The identifier of the file upload.
- `FileUpload` (FileUpload): Navigation property to the file upload.
- `DataCollection` (DataCollection?): Navigation property to the data collection.
- `DataCollectionId` (string?): The identifier of the data collection.
- `RowNumber` (int): The row number.
- `SampleYear` (int): The sample year.
- `SampleMonth` (int): The sample month.
- `SurveyParticipant` (SurveyParticipant?): Navigation property to the survey participant.
- `SurveyParticipantId` (int?): The identifier of the survey participant.
- `IsValid` (bool): Indicates if the record is valid.
- `IsDuplicate` (bool): Indicates if the record is a duplicate.
- `IsEligible` (bool): Indicates if the record is eligible.
- `DeletedOn` (DateTime?): The date the record was deleted.
- `Sample` (Sample?): Navigation property to the sample.

---

## LogType

Represents the type of a log entry.

**Values:**

- `Unknown`: 0
- `Information`: 1
- `Warning`: 2
- `Error`: 3

---

## RawCallData

Represents raw data from a call.

**Properties:**

- `Id` (long): The unique identifier for the raw call data.
- `CaseId` (string): The case identifier.
- `SIni` (string?): The interviewer's initials.
- `STel` (string?): The telephone number.
- `SLan` (int?): The language of the interview.
- `SDat` (DateTime?): The date of the interview.
- `ResIntervCall` (string?): The result of the interview call.
- `SHrd` (TimeSpan?): The duration of the interview.
- `SDus` (int?): The number of survey questions answered.
- `SDur` (int?): The duration of the survey.
- `SDnq` (int?): The number of questions not answered.
- `SApp` (int?): The appointment status.
- `SRes` (string?): The result of the survey.
- `TZone` (int?): The time zone.
- `ContactIntro` (int?): The contact introduction.
- `TargetID` (string): The target identifier.
- `Mkt` (int?): The market.
- `Phone` (string?): The phone number.
- `Lang` (string?): The language.
- `CareGiverN` (string?): The name of the caregiver.
- `DecedentN` (string?): The name of the decedent.
- `Ntro1` (int?): The introduction.
- `NProX` (int?): The proxy status.
- `Int78` (int?): The interviewer's gender.
- `Int77` (int?): The interviewer's age.
- `INT01` (string?): The interviewer's ID.
- `Dnc` (string?): The do not call status.
- `Tel01` (string?): The telephone number.
- `Cont` (string?): The contact status.
- `Cont1` (int?): The contact status.
- `CTim1` (string?): The contact time.
- `Proxy` (int?): The proxy status.
- `AskforProxy` (int?): The ask for proxy status.
- `ProxyN` (string?): The name of the proxy.
- `Q1` (string?): The answer to question 1.
- `Q1A` (string?): The answer to question 1A.
- `O_Q1A` (string?): The other answer to question 1A.
- `Q2A` (string?): The answer to question 2A.
- `Q2B` (string?): The answer to question 2B.
- `Q2C` (string?): The answer to question 2C.
- `Q2D` (string?): The answer to question 2D.
- `Q2E` (string?): The answer to question 2E.
- `Q2F` (string?): The answer to question 2F.
- `Q2G` (string?): The answer to question 2G.
- `O_Q2G` (string?): The other answer to question 2G.
- `Q3` (string?): The answer to question 3.
- `Q4` (string?): The answer to question 4.
- `Q5` (string?): The answer to question 5.
- `Q6` (string?): The answer to question 6.
- `Q7` (string?): The answer to question 7.
- `Q8` (string?): The answer to question 8.
- `Q9` (string?): The answer to question 9.
- `Q10` (string?): The answer to question 10.
- `Q11` (string?): The answer to question 11.
- `Q12` (string?): The answer to question 12.
- `Q13` (string?): The answer to question 13.
- `Q14` (string?): The answer to question 14.
- `Q15` (string?): The answer to question 15.
- `Q16` (string?): The answer to question 16.
- `Q17` (string?): The answer to question 17.
- `Q18` (string?): The answer to question 18.
- `Q19` (string?): The answer to question 19.
- `Q20` (string?): The answer to question 20.
- `Q21` (string?): The answer to question 21.
- `Q22` (string?): The answer to question 22.
- `Q23` (string?): The answer to question 23.
- `Q24` (string?): The answer to question 24.
- `Q25` (string?): The answer to question 25.
- `Q26` (string?): The answer to question 26.
- `Q27` (string?): The answer to question 27.
- `Q28` (string?): The answer to question 28.
- `Q29` (string?): The answer to question 29.
- `Q30` (string?): The answer to question 30.
- `Q31` (string?): The answer to question 31.
- `Q32` (string?): The answer to question 32.
- `Q33` (string?): The answer to question 33.
- `Q34` (string?): The answer to question 34.
- `Q35` (string?): The answer to question 35.
- `Q36` (string?): The answer to question 36.
- `Q37` (string?): The answer to question 37.
- `Q38` (string?): The answer to question 38.
- `Q39` (string?): The answer to question 39.
- `Q40` (string?): The answer to question 40.
- `Q41` (string?): The answer to question 41.
- `Q42` (string?): The answer to question 42.
- `Q42A` (string?): The answer to question 42A.
- `Q43` (string?): The answer to question 43.
- `Q43A` (string?): The answer to question 43A.
- `Q43B` (string?): The answer to question 43B.
- `Q43C` (string?): The answer to question 43C.
- `Q43D` (string?): The answer to question 43D.
- `Q43E` (string?): The answer to question 43E.
- `Q44` (string?): The answer to question 44.
- `Q45` (string?): The answer to question 45.
- `Q46` (string?): The answer to question 46.
- `Q47` (string?): The answer to question 47.
- `Q47A` (string?): The answer to question 47A.
- `O_Q47A` (string?): The other answer to question 47A.
- `Q48` (string?): The answer to question 48.
- `O_Q48` (string?): The other answer to question 48.
- `Q48A` (string?): The answer to question 48A.
- `Q49` (string?): The answer to question 49.
- `Q50` (string?): The answer to question 50.
- `Q51` (string?): The answer to question 51.
- `Q52` (string?): The answer to question 52.
- `Q53` (string?): The answer to question 53.
- `Q54` (string?): The answer to question 54.
- `Q55` (string?): The answer to question 55.
- `Q56` (string?): The answer to question 56.
- `Q57` (string?): The answer to question 57.
- `OriginRowNumber` (int): The row number in the import file.
- `OriginImportId` (string): ID of the import file in the CallDataImport table.
- `OriginImport` (CallDataImport?): Navigation property to the original import.
- `ImportedDate` (DateTime): The date the data was imported.
- `ModifiedDate` (DateTime?): The date the data was modified.
- `ProcessingStatusId` (int): The identifier of the processing status.
- `VendorDispositionId` (int?): The identifier of the vendor disposition.
- `IsComplete` (bool?): Indicates if the call is complete.
- `IsBest` (bool?): Indicates if the call is the best.
- `IsAdverse` (bool?): Indicates if the call is adverse.
- `IsVeteran` (bool?): Indicates if the person is a veteran.
- `InBenchmark` (bool?): Indicates if the call is in the benchmark.
- `IsLateCollection` (bool?): Indicates if the call is a late collection.
- `IsBlank` (bool?): Indicates if the call is blank.
- `Questions` (Lazy<Dictionary<string, IQuestion>>?): The questions and answers.
- `BarcodeString` (string?): The barcode string.
- `CallDateTime` (DateTime): The date and time of the call.

---

## RawScanData

Represents raw data from a scan.

**Properties:**

- `Id` (long): The unique identifier for the raw scan data.
- `Q1` (int?): The answer to question 1.
- `Q1a` (string?): The answer to question 1a.
- `Q1i` (string?): The answer to question 1i.
- `Q2` (string?): The answer to question 2.
- `Q2a` (string?): The answer to question 2a.
- `Q2i` (string?): The answer to question 2i.
- `Q3` (string?): The answer to question 3.
- `TrackingId11` (string?): The tracking ID 11.
- `TrackingId12` (string?): The tracking ID 12.
- `Q4` (string?): The answer to question 4.
- `Q5` (string?): The answer to question 5.
- `Q6` (string?): The answer to question 6.
- `Q7` (string?): The answer to question 7.
- `Q8` (string?): The answer to question 8.
- `Q9` (string?): The answer to question 9.
- `Q10` (string?): The answer to question 10.
- `Q11` (string?): The answer to question 11.
- `Q12` (string?): The answer to question 12.
- `Q13` (string?): The answer to question 13.
- `Q14` (string?): The answer to question 14.
- `Q15` (string?): The answer to question 15.
- `Q16` (string?): The answer to question 16.
- `Q17` (string?): The answer to question 17.
- `Q18` (string?): The answer to question 18.
- `Q19` (string?): The answer to question 19.
- `Q20` (string?): The answer to question 20.
- `TrackingId21` (string?): The tracking ID 21.
- `TrackingId22` (string?): The tracking ID 22.
- `Q21` (string?): The answer to question 21.
- `Q22` (string?): The answer to question 22.
- `Q23` (string?): The answer to question 23.
- `Q24` (string?): The answer to question 24.
- `Q25` (string?): The answer to question 25.
- `Q26` (string?): The answer to question 26.
- `Q27` (string?): The answer to question 27.
- `Q28` (string?): The answer to question 28.
- `Q29` (string?): The answer to question 29.
- `Q30` (string?): The answer to question 30.
- `Q31` (string?): The answer to question 31.
- `Q32` (string?): The answer to question 32.
- `Q33` (string?): The answer to question 33.
- `Q34` (string?): The answer to question 34.
- `Q35` (string?): The answer to question 35.
- `Q36` (string?): The answer to question 36.
- `Q37` (string?): The answer to question 37.
- `Q38` (string?): The answer to question 38.
- `Q39` (string?): The answer to question 39.
- `Q40` (string?): The answer to question 40.
- `Q41` (string?): The answer to question 41.
- `Q42` (string?): The answer to question 42.
- `Q43` (string?): The answer to question 43.
- `Q44` (string?): The answer to question 44.
- `Q45` (string?): The answer to question 45.
- `Q46` (string?): The answer to question 46.
- `Q47` (string?): The answer to question 47.
- `Q47a` (string?): The answer to question 47a.
- `Q47i` (string?): The answer to question 47i.
- `Q48` (string?): The answer to question 48.
- `QS2a` (string?): The answer to question S2a.
- `QS2` (string?): The answer to question S2.
- `V1` (string?): The answer to question V1.
- `V2` (string?): The answer to question V2.
- `V3` (string?): The answer to question V3.
- `V3a` (string?): The answer to question V3a.
- `V3b` (string?): The answer to question V3b.
- `V4` (string?): The answer to question V4.
- `V5` (string?): The answer to question V5.
- `V6` (string?): The answer to question V6.
- `CreatedDate` (DateTime): The date the data was created.
- `CreatedUser` (string): The user who created the data.
- `CreatedMachine` (string): The machine that created the data.
- `TrackingID31` (string?): The tracking ID 31.
- `TrackingID32` (string?): The tracking ID 32.
- `DispositionIds` (string): The disposition IDs.
- `Page1Image` (string?): The image of page 1.
- `Page2Image` (string?): The image of page 2.
- `Page3Image` (string?): The image of page 3.
- `Page4Image` (string?): The image of page 4.
- `IsComplete` (bool?): Indicates if the scan is complete.
- `IsBest` (bool?): Indicates if the scan is the best.
- `IsAdverse` (bool?): Indicates if the scan is adverse.
- `IsVeteran` (bool?): Indicates if the person is a veteran.
- `InBenchmark` (bool?): Indicates if the scan is in the benchmark.
- `IsLateCollection` (bool?): Indicates if the scan is a late collection.
- `IsBlank` (bool?): Indicates if the scan is blank.
- `TrackingID41` (string?): The tracking ID 41.
- `TrackingID42` (string?): The tracking ID 42.
- `Questions` (Lazy<Dictionary<string, IQuestion>>?): The questions and answers.
- `HasPageBarcodes` (bool): Indicates if the scan has page barcodes.
- `PageBarcodesMatch` (bool): Indicates if the page barcodes match.
- `TrackingID` (string?): The tracking ID.
- `BarcodeString` (string?): The barcode string.

---

## Sample

Represents a sample.

**Properties:**

- `Id` (int): The unique identifier for the sample.
- `TrackingID` (string): The tracking ID.
- `FinalDispositionId` (int): The final disposition ID.
- `DataCollection` (DataCollection): Navigation property to the data collection.
- `DataCollectionId` (string): The identifier of the data collection.
- `ClientSurvey` (ClientSurvey): Navigation property to the client survey.
- `ClientSurveyId` (string): The identifier of the client survey.
- `SourceUploadRecord` (FileUploadRecord): Navigation property to the source upload record.
- `SourceUploadRecordId` (int): The identifier of the source upload record.
- `RawScanData` (RawScanData?): Navigation property to the raw scan data.
- `RawScanDataId` (long?): The identifier of the raw scan data.
- `RawCallData` (RawCallData?): Navigation property to the raw call data.
- `RawCallDataId` (long?): The identifier of the raw call data.
- `IsReportable` (bool): Indicates if the sample is reportable.
- `MetCollectionEnd` (bool): Indicates if the sample met the collection end.
- `ConsentToShare` (bool): Indicates if the sample has consent to share.
- `MissingAddress` (bool): Indicates if the address is missing.
- `MissingPhone` (bool): Indicates if the phone number is missing.
- `IsSelectedForSample` (bool): Indicates if the sample was selected for the sample.
- `RandomSort` (double?): The random sort value.
- `WaveOneInternalDispositionId` (int): The wave one internal disposition ID.
- `WaveOneDataFirstReceivedDate` (DateTime?): The date the wave one data was first received.
- `WaveTwoInternalDispositionId` (int): The wave two internal disposition ID.
- `WaveTwoDataFirstReceivedDate` (DateTime?): The date the wave two data was first received.
- `CreatedOn` (DateTime): The date the sample was created.
- `ModifiedOn` (DateTime?): The date the sample was modified.
- `DeletedOn` (DateTime?): The date the sample was deleted.
- `SurveyResults` (List<SurveyResult>): Navigation property to the survey results.

---

## SampleMonth

Represents a sample month.

**Properties:**

- `Id` (string): The unique identifier for the sample month.
- `Year` (int): The year of the sample month.
- `Month` (int): The month of the sample month.
- `MonthYear` (DateOnly): The month and year of the sample month.
- `Status` (SampleMonthProcessingStatus): The status of the sample month.
- `ProgramType` (CahpsService): Navigation property to the program type.
- `ProgramTypeId` (int): The identifier of the program type.
- `FileSubmissionStartDate` (DateOnly): The start date for file submission.
- `FileSubmissionDueDate` (DateOnly): The due date for file submission.
- `WaveOneBatchDate` (DateOnly): The date of the wave one batch.
- `WaveOneDataCollectionStartDate` (DateOnly): The start date of the wave one data collection.
- `WaveTwoBatchDate` (DateOnly): The date of the wave two batch.
- `WaveTwoDataCollectionStartDate` (DateOnly): The start date of the wave two data collection.
- `DataCollectionEndDate` (DateOnly): The end date of the data collection.

---

## State

Represents a state.

**Properties:**

- `PostalCode` (string): The postal code of the state.
- `FedID` (string): The federal ID of the state.
- `StateName` (string): The name of the state.
- `Region` (int): The region of the state.

---

## SurveyParticipant

Represents a survey participant. *This is the source of name and address information to be included in the batch.*

**Properties:**

- `Id` (int): The unique identifier for the survey participant.
- `CahpsService` (CahpsService): Navigation property to the CAHPS service.
- `CahpsServiceId` (int): The identifier of the CAHPS service.
- `GivenName` (string): The given name of the participant.
- `AdditionalName` (string?): The additional name of the participant.
- `FamilyName` (string): The family name of the participant.
- `Address1` (string?): The first line of the address.
- `Address2` (string?): The second line of the address.
- `City` (string?): The city of the address.
- `State` (string?): The state of the address.
- `Zip` (string?): The zip code of the address.
- `Phone1` (string?): The first phone number.
- `Phone2` (string?): The second phone number.
- `Phone3` (string?): The third phone number.
- `Email1` (string?): The email address.
- `PreferredLanguage` (CahpsServiceLanguage): Navigation property to the preferred language.
- `PreferredLanguageId` (int): The identifier of the preferred language.
- `MissingAddress` (bool): Indicates if the address is missing.
- `MissingPhone` (bool): Indicates if the phone number is missing.
- `CreatedOn` (DateTime): The date the participant was created.
- `ModifiedOn` (DateTime?): The date the participant was modified.
- `DeletedOn` (DateTime?): The date the participant was deleted.

---

## SurveyResult

Represents a survey result.

**Properties:**

- `Id` (int): The unique identifier for the survey result.
- `SampleId` (int): The identifier of the sample.
- `Sample` (Sample): Navigation property to the sample.
- `QuestionResponseId` (string): The identifier of the question response.
- `QuestionResponse` (QuestionResponse): Navigation property to the question response.
- `RawValue` (string?): The raw value of the response.

---

## User

Represents a user.

**Properties:**

- `Id` (string): The unique identifier for the user.
- `GivenName` (string): The given name of the user.
- `FamilyName` (string): The family name of the user.
- `Email` (string): The email address of the user.
- `UserName` (string): The username of the user.
- `ManagerId` (string?): The identifier of the user's manager.
- `DeletedAt` (DateTime?): The date the user was deleted.
- `SysUser` (bool): Indicates if the user is a system user.
- `SysUserDescription` (string?): The description of the system user.
- `UserClients` (List<UserClient>): Navigation property to the user's clients.
- `CahpsUserOptions` (CahpsUserOptions?): Navigation property to the user's CAHPS options.

---

## UserClient

Represents the relationship between a user and a client.

**Properties:**

- `UserId` (string): The identifier of the user.
- `User` (User): Navigation property to the user.
- `ClientId` (string): The identifier of the client.
- `Client` (Client): Navigation property to the client.

---

## DataManager/PhoneNumberUpdate

*Class Only, no DB Table* Represents a phone number update performed via the data manager. 

**Properties:**

- `SampleID` (string): The sample ID.
- `Phone1` (string): The phone number.

---

## Surveys/Question

Represents a question in a survey template.

**Properties:**

- `Id` (string): The unique identifier for the question.
- `Type` (QuestionType): The type of the question.
- `Text` (string): The text of the question.
- `Abbrev` (string): The abbreviation of the question.
- `Responses` (List<QuestionResponse>): Navigation property to the question responses.

---

## Surveys/QuestionResponse

Represents an available response to a question in a survey template.

**Properties:**

- `Id` (string): The unique identifier for the response.
- `Question` (Question): Navigation property to the question.
- `QuestionId` (string): The identifier of the question.
- `Value` (string): The value of the response.
- `Label` (string): The label of the response.
- `Sort` (double): The sort order of the response.

---

## Surveys/QuestionType

Represents the type of a question.

**Values:**

- `Unknown`: 0
- `SingleSelect`: 1
- `MultiSelect`: 2
- `Text`: 3

---

## Surveys/Survey

Represents a survey template.

**Properties:**

- `Id` (string): The unique identifier for the survey.
- `SurveyCode` (string): The code of the survey.
- `Name` (string): The name of the survey.
- `ProgramTypeId` (int): The identifier of the program type.
- `ProgramType` (CahpsService): Navigation property to the program type.
- `ParentSurveyId` (string?): The identifier of the parent survey.
- `ParentSurvey` (Survey?): Navigation property to the parent survey.

---

## Surveys/SurveyQuestion

Represents the relationship between a survey and a question.

**Properties:**

- `SurveyId` (string): The identifier of the survey.
- `Survey` (Survey): Navigation property to the survey.
- `QuestionId` (string): The identifier of the question.
- `Question` (Question): Navigation property to the question.
- `Group` (SurveyQuestionGroup): Navigation property to the survey question group.
- `GroupId` (string): The identifier of the survey question group.
- `Sort` (double): The sort order.
- `Aliases` (string): The aliases for the question.

---

## Surveys/SurveyQuestionGroup

Represents a group of questions in a survey.

**Properties:**

- `Id` (string): The unique identifier for the group.
- `Text` (string): The text of the group.
- `Description` (string?): The description of the group.
- `Sort` (double): The sort order.

---

## Xmls/CaregiverResponseSet

*Class Only, no DB Table* Represents a set of caregiver responses in the XML data.

**Properties:**

- `ProviderId` (string?): The provider ID.
- `DecedentId` (string?): The decedent ID.
- `Related` (string?): The relationship to the decedent.
- `LocationHome` (string?): The location of care was home.
- `LocationAssisted` (string?): The location of care was assisted living.
- `LocationNursingHome` (string?): The location of care was a nursing home.
- `LocationHospital` (string?): The location of care was a hospital.
- `LocationHospiceFacility` (string?): The location of care was a hospice facility.
- `LocationOther` (string?): The location of care was other.
- `Oversee` (string?): The caregiver oversaw the care.
- `NeedHelp` (string?): The caregiver needed help.
- `GetHelp` (string?): The caregiver got help.
- `HospiceInformTime` (string?): The hospice informed the caregiver in a timely manner.
- `HelpAsNeeded` (string?): The caregiver got help as needed.
- `HospiceExplained` (string?): The hospice explained things well.
- `HospiceInformed` (string?): The hospice kept the caregiver informed.
- `HospiceConfused` (string?): The hospice was confusing.
- `TreatWithDignity` (string?): The hospice treated the patient with dignity.
- `HospiceCared` (string?): The hospice cared for the patient.
- `HospiceTalked` (string?): The hospice talked to the patient.
- `HospiceListened` (string?): The hospice listened to the patient.
- `PainSuffer` (string?): The patient suffered from pain.
- `PainHelp` (string?): The patient got help for pain.
- `PainMeds` (string?): The patient got pain medication.
- `PainMedsSideffects` (string?): The patient had side effects from pain medication.
- `PainMedsWatch` (string?): The hospice watched for side effects from pain medication.
- `PainMedsTraining` (string?): The hospice provided training for pain medication.
- `Breathing` (string?): The patient had trouble breathing.
- `BreathHelp` (string?): The patient got help for breathing.
- `BreathTraining` (string?): The hospice provided training for breathing.
- `Constipation` (string?): The patient had constipation.
- `ConstipationHelp` (string?): The patient got help for constipation.
- `Sadness` (string?): The patient had sadness.
- `SadnessHelp` (string?): The patient got help for sadness.
- `Restlessness` (string?): The patient had restlessness.
- `RestlessTraining` (string?): The hospice provided training for restlessness.
- `MovingTraining` (string?): The hospice provided training for moving.
- `ExpectationInfo` (string?): The hospice provided information about what to expect.
- `ReceivedNursingHome` (string?): The patient received care in a nursing home.
- `CooperateNursingHome` (string?): The hospice cooperated with the nursing home.
- `DifferentNursingHome` (string?): The hospice was different from the nursing home.
- `HospiceCarefulListen` (string?): The hospice listened carefully.
- `BeliefRespect` (string?): The hospice respected the patient's beliefs.
- `EmotionalSupport` (string?): The hospice provided emotional support.
- `EmotionalAfter` (string?): The hospice provided emotional support after the patient's death.
- `RateHospice` (string?): The rating of the hospice.
- `LikelyRecommend` (string?): The likelihood of recommending the hospice.
- `DecedentEducation` (string?): The decedent's education.
- `DecedentLatino` (string?): The decedent was Latino.
- `RaceNativeAmerican` (string?): The decedent was Native American.
- `RaceAsian` (string?): The decedent was Asian.
- `RaceAfricanAmerican` (string?): The decedent was African American.
- `RacePacificIslander` (string?): The decedent was a Pacific Islander.
- `RaceWhite` (string?): The decedent was White.
- `CaregiverAge` (string?): The caregiver's age.
- `CaregiverGender` (string?): The caregiver's gender.
- `CaregiverEducation` (string?): The caregiver's education.
- `CaregiverHomeLanguage` (string?): The caregiver's home language.

---

## Xmls/DecedentLevelInfo

*Class Only, no DB Table* Represents decedent-level information in the XML data.

**Properties:**

- `ProviderId` (string?): The provider ID.
- `DecedentId` (string?): The decedent ID.
- `BirthYear` (string?): The birth year of the decedent.
- `BirthMonth` (string?): The birth month of the decedent.
- `BirthDay` (string?): The birth day of the decedent.
- `DeathYear` (string?): The death year of the decedent.
- `DeathMonth` (string?): The death month of the decedent.
- `DeathDay` (string?): The death day of the decedent.
- `AdmissionYear` (string?): The admission year of the decedent.
- `AdmissionMonth` (string?): The admission month of the decedent.
- `AdmissionDay` (string?): The admission day of the decedent.
- `DecedentGender` (string?): The gender of the decedent.
- `DecedentHispanic` (string?): The decedent was Hispanic.
- `DecedentRace` (string?): The race of the decedent.
- `CaregiverRelationship` (string?): The relationship of the caregiver to the decedent.
- `DecedentPayerPrimary` (string?): The primary payer of the decedent.
- `DecedentPayerSecondary` (string?): The secondary payer of the decedent.
- `DecedentPayerOther` (string?): The other payer of the decedent.
- `LastCareLocation` (string?): The last care location of the decedent.
- `FacilityName` (string?): The name of the facility.
- `DecedentPrimaryDiagnosis` (string?): The primary diagnosis of the decedent.
- `SurveyStatus` (string?): The status of the survey.
- `SurveyCompletionMode` (string?): The completion mode of the survey.
- `NumberAttemptsPhone` (string?): The number of phone attempts.
- `NumberAttemptsMail` (string?): The number of mail attempts.
- `SurveyLanguage` (string?): The language of the survey.
- `ResponseLagTime` (string?): The response lag time.
- `SupplimentalQuestionCount` (string?): The number of supplemental questions.
- `CaregiverResponse` (CaregiverResponseSet?): The caregiver response set.

---

## Xmls/HospiceHeader

*Class Only, no DB Table* Represents the hospice header in the XML data.

**Properties:**

- `ReferenceYear` (string?): The reference year.
- `ReferenceMonth` (string?): The reference month.
- `ProviderName` (string?): The name of the provider.
- `ProviderId` (string?): The ID of the provider.
- `NPI` (string?): The NPI of the provider.
- `SurveyMode` (string?): The survey mode.
- `TotalDecedentCount` (string?): The total number of decedents.
- `LiveDischargeCount` (string?): The number of live discharges.
- `NoPublicityCount` (string?): The number of no publicity requests.
- `MissingDatesOfDeath` (string?): The number of missing dates of death.
- `RecordsSubmitted` (string?): The number of records submitted.
- `IneligiblePreSample` (string?): The number of ineligible pre-sample.
- `AvailableSample` (string?): The number of available samples.
- `SampledCases` (string?): The number of sampled cases.
- `SampleSize` (string?): The sample size.
- `IneligiblePostSample` (string?): The number of ineligible post-sample.
- `SampleType` (string?): The sample type.
- `HospiceOffices` (string?): The number of hospice offices.

---
