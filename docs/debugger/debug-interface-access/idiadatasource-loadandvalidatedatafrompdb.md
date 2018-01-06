---
title: 'Idiadatasource:: Loadandvalidatedatafrompdb | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bcd82116c7499d2a2289fc0c198a2be053226721
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
Wird geöffnet und überprüft, ob die Programmdatenbankdatei (.pdb) bereitgestellte Signaturinformationen übereinstimmt, und bereitet die PDB-Datei als Datenquelle Debuggen.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdbPath`  
 [in] Der Pfad zur PDB-Datei.  
  
 `pcsig70`  
 [in] Der GUID-Signatur für die Signatur der PDB-Datei zu überprüfen. Nur die PDB-Dateien im [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] und später GUID-Signaturen aufweisen.  
  
 `sig`  
 [in] Die 32-Bit-Signatur für die Signatur der PDB-Datei zu überprüfen.  
  
 `age`  
 [in] Alter-Wert, um zu überprüfen. Das Alter entspricht nicht unbedingt alle bekannten Time-Werten, er wird verwendet, um zu bestimmen, ob eine PDB-Datei mit einer entsprechenden .exe-Datei synchron ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben. Die folgende Tabelle zeigt die möglichen Rückgabewerte für diese Methode.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Fehler beim Öffnen der Datei, oder die Datei weist ein ungültiges Format.|  
|E_PDB_FORMAT|Es wurde versucht, Zugriff auf eine Datei mit der ein veraltetes Format.|  
|E_PDB_INVALID_SIG|Signatur stimmt nicht überein.|  
|E_PDB_INVALID_AGE|Alter stimmt nicht überein.|  
|E_INVALIDARG|Ungültiger Parameter.|  
|E_UNEXPECTED|Die Datenquelle wurde bereits vorbereitet wurde.|  
  
## <a name="remarks"></a>Hinweise  
 Eine PDB-Datei enthält die Signatur und Age-Werte. Diese Werte werden in .exe oder .dll-Datei repliziert, die PDB-Datei entspricht. Vor dem Vorbereiten der Datenquelle, überprüft diese Methode an, dass die Signatur und Alter der benannten PDB-Datei die bereitgestellten Werte entsprechen.  
  
 Verwenden Sie zum Laden einer PDB-Datei ohne Überprüfung der [idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) Methode.  
  
 Verwenden Sie zum Laden von Daten (durch einen Rückrufmechanismus) Zugriff auf die [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode.  
  
 Um eine PDB-Datei direkt aus dem Arbeitsspeicher zu laden, verwenden die [idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) Methode.  
  
## <a name="example"></a>Beispiel  
  
```C++  
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
  
## <a name="see-also"></a>Siehe auch  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)