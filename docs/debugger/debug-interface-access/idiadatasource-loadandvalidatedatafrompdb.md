---
title: "IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaDataSource::loadAndValidateDataFromPdb-Methode"
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Öffnet und überprüft, dass die Programmdatenbankdatei \(.pdb\) die jeweiligen Signaturinformationen übereinstimmt, und bereitet die PDB\-Datei als die Datenquelle vor.  
  
## Syntax  
  
```cpp#  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### Parameter  
 `pdbPath`  
 \[in\]  Der Pfad zur PDB\-Datei.  
  
 `pcsig70`  
 \[in\]  Die für die PDB\-Datei\-Unterzeichnung zu überprüfen, GUID\-Unterzeichnung.  Nur [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] in PDB\-Dateien verfügen und später GUID\-Unterzeichnungen.  
  
 `sig`  
 \[in\]  Die für die PDB\-Datei\-Unterzeichnung zu überprüfen, 32\-Bit\-Unterzeichnung.  
  
 `age`  
 \[in\]  Der zu überprüfende Wert des Alters.  Das Alter nicht notwendigerweise entspricht einem bekannten Uhrzeitwert, der verwendet wird, um zu bestimmen, ob eine PDB\-Datei mit einer entsprechenden EXE\-Datei nicht synchronisiert ist.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  In der folgenden Tabelle werden die möglichen Rückgabewerte für diese Methode auf.  
  
|Wert|Beschreibung|  
|----------|------------------|  
|E\_PDB\_NOT\_FOUND|Fehlgeschlagene, die Datei oder die Datei geöffnet hat ein ungültiges Format.|  
|E\_PDB\_FORMAT|Versucht, eine Datei mit einem veralteten Format zuzugreifen.|  
|E\_PDB\_INVALID\_SIG|Signatur stimmen nicht überein.|  
|E\_PDB\_INVALID\_AGE|Alter stimmen nicht überein.|  
|E\_INVALIDARG|Ungültiger Parameter.|  
|E\_UNEXPECTED|Die Datenquelle ist bereits vorbereitet wurde.|  
  
## Hinweise  
 Eine PDB\-Datei Alters und Signatur enthält.  Diese Werte werden im EXE\- oder DLL\-Datei repliziert, das die PDB\-Datei übereinstimmt.  Bevor sie die Datenquelle vorbereitet, überprüft diese Methode, ob der benannten .pdb\-die Signatur und das Alter Datei die bereitgestellten Werte übereinstimmt.  
  
 Um eine PDB\-Datei ohne Validierung zu laden, verwenden Sie die [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)\-Methode.  
  
 Um zum ladevorgang Daten zugreifen zu können \(durch einen Rückrufmechanismus\), verwenden Sie die [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)\-Methode.  
  
 Um eine PDB\-Datei direkt aus dem Arbeitsspeicher zu laden, verwenden Sie die [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)\-Methode.  
  
## Beispiel  
  
```cpp#  
IDiaDataSource* pSource;  // Previously created data source.  
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);  
DWORD expectedFileSignature = 0x12345678;  
DWORD expectedAge           = 128;  
  
HRESULT hr;  
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",  
                                          &expectedGUIDSignature,  
                                          expectedFileSignature,  
                                          expectedAge);  
if (FAILED(hr))  
{  
    // Report an error  
}  
  
```  
  
## Siehe auch  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)