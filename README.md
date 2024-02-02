# UID (User Identifier)
UID to provide capability to uniquely identify a wide variety of items. 

They guarantee uniqueness across multiple countries, sites, vendors and equipment. Different classes of objects, instance of objects and information entities can be distinguished from one another across the DICOM universe of discourse irrespective of any semantic context.
    
UID identification scheme is based on the OSI Object Identification (ISO 8824 standard)
    
All Unique Identifiers, used within the context of the DICOM Standard, are registered values as defined by ISO 9834-1 to ensure global uniqueness.
    
Each UID is composed of two parts, an <org root> and a <suffix> in numeric term
    
    UID = <org root>.<suffix>
    
**<org root>** identifies an organizations (i.e manucfacturer, research organization, NEMA, etc)
    
**<suffix>** shall be unique within the scope of the <org root>.

## UID encoding rules

1. the first digit of each component shall not be zero 
    e.g “00029” would be “29”
2. each component numeric value shall be encoded using the characters 0-9 
3. Components shall be separated by the character “.”
4. UIDs, shall not exceed 64 total characters, including the digits of each component, separator between components, and the NULL padding character if needed
5. If ending on an odd byte boundary, except when used for network negotiation (see [PS3.8](https://dicom.nema.org/dicom/2013/output/chtml/part08/PS3.8.html)), one trailing NULL (00H), as a padding character, shall follow the last component in order to align the UID on an even byte boundary.
6. <suffix> could include:
    - product
    - system identifier
    - study, series and image numbers
    - study, series and image data & times

# example UID

- by ISO member body ⇒ 1.2.840.xxxxx
    1 identifies ISO
    2 identifies the ISO member body branch
    840 identifies the country cod eod a specific ISO member body (US for ANSI)
    xxxx identifies a specific organization as registered by the ISO member body ANSI
    
- by ISO ⇒ 1.3.yyyy
    1 identifies ISO
    3 identifies the international branch
    yyyy identifies a specific organization as registered by an internasional code designator registrations authority

# Types of UID
1. Series Instance UID: This identifier is assigned to each image series within a study. It distinguishes one image series from another series within the same study. A series of images consists of multiple slices taken from various angles and depths.

2. SOP Class UID: This identifier specifies the type or class of an SOP (Service-Object Pair) object in a DICOM file. It indicates the type of data or information stored in the DICOM file. For example, the SOP Class UID for a CT image is different from the SOP Class UID for an MRI image.

3. SOP Instance UID: This identifier is assigned to each instance of an SOP object in a DICOM file. It distinguishes one instance of an SOP object from another instance of the same type.

4. Study Instance UID: This identifier is used to uniquely identify one study or one medical test performed on one patient.


# Example Case

There are 2 CT image scans from 2 different patients:

- Both images have the same SOP Class UID, indicating that they are both CT images.
- However, the SOP Instance UID will be different between the two images because each represents a different instance of the same SOP object.
- Meanwhile, the Series Instance UID will also be different for the two images because each Series Instance UID represents a series of images consisting of different slices with varying depths and angles. Series Instance UID allows for unique identification of each image series within one study.
- Additionally, each CT scan will have its own Study Instance UID, which uniquely identifies each entire study or medical test conducted on a patient.

source:
https://dicom.nema.org/dicom/2013/output/chtml/part05/chapter_9.html
https://dicom.nema.org/dicom/2013/output/chtml/part05/chapter_C.html 
https://dicom.nema.org/dicom/2013/output/chtml/part05/sect_6.2.html#table_6.2-1