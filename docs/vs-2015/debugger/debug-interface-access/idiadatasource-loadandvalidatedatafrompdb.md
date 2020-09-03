---
title: 'IDiaDataSource:: loadAndValidateDataFromPdb | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f19a910af45ed70ae74c72441890ecae6c81d2a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198630"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Öffnet und überprüft, ob die Programm Datenbankdatei (PDB-Datei) mit den bereitgestellten Signatur Informationen übereinstimmt, und bereitet die PDB-Datei als debugdatenquelle vor.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdbPath`  
 in Der Pfad zur PDB-Datei.  
  
 `pcsig70`  
 in Die GUID-Signatur, die anhand der PDB-Datei Signatur überprüft werden soll. Nur PDB-Dateien in [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] und höher verfügen über GUID-Signaturen.  
  
 `sig`  
 in Die 32-Bit-Signatur, die anhand der PDB-Datei Signatur überprüft werden soll.  
  
 `age`  
 in Der zu überprüfende Alters Wert. Das Alter entspricht nicht notwendigerweise einem bekannten Uhrzeitwert. es wird verwendet, um zu bestimmen, ob eine PDB-Datei mit einer entsprechenden exe-Datei nicht synchronisiert ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. In der folgenden Tabelle sind die möglichen Rückgabewerte für diese Methode aufgeführt.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Die Datei konnte nicht geöffnet werden, oder die Datei weist ein ungültiges Format auf.|  
|E_PDB_FORMAT|Es wurde versucht, auf eine Datei mit einem veralteten Format zuzugreifen.|  
|E_PDB_INVALID_SIG|Signatur stimmt nicht mit ab.|  
|E_PDB_INVALID_AGE|Das Alter stimmt nicht mit.|  
|E_INVALIDARG|Ungültiger Parameter.|  
|E_UNEXPECTED|Die Datenquelle wurde bereits vorbereitet.|  
  
## <a name="remarks"></a>Bemerkungen  
 Eine PDB-Datei enthält sowohl Signatur-als auch Alters Werte. Diese Werte werden in der exe-oder DLL-Datei repliziert, die mit der PDB-Datei übereinstimmt. Vor dem Vorbereiten der Datenquelle überprüft diese Methode, ob die Signatur und das Alter der benannten PDB-Datei mit den angegebenen Werten identisch sind.  
  
 Wenn Sie eine PDB-Datei ohne Validierung laden möchten, verwenden Sie die [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) -Methode.  
  
 Verwenden Sie die Methode [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) , um Zugriff auf den Daten Ladevorgang zu erhalten (über einen Rückrufmechanismus).  
  
 Verwenden Sie die [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) -Methode, um eine PDB-Datei direkt aus dem Arbeitsspeicher zu laden.  
  
## <a name="example"></a>Beispiel  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
