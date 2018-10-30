---
title: 'Idiadatasource:: Loadandvalidatedatafrompdb | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40d25345853474b3d12f722dc0aa05cc6726d506
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856639"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wird geöffnet und überprüft, ob die Programmdatenbankdatei (.pdb) der bereitgestellten Signaturinformationen entspricht, und bereitet die PDB-Datei als Datenquelle Debuggen.  
  
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
 [in] Der Pfad zur PDB-Datei.  
  
 `pcsig70`  
 [in] Die GUID-Signatur der Signatur der PDB-Datei überprüft werden soll. Nur PDB-Dateien im [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] und später GUID-Signaturen aufweisen.  
  
 `sig`  
 [in] Die 32-Bit-Signatur der Signatur der PDB-Datei überprüft werden soll.  
  
 `age`  
 [in] Age-Wert, um zu überprüfen. Das Alter entspricht nicht notwendigerweise alle bekannten Time-Werten, er wird verwendet, um zu bestimmen, ob eine PDB-Datei mit einer entsprechenden .exe-Datei synchron sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Die folgende Tabelle zeigt die möglichen Rückgabewerte für diese Methode.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Fehler beim Öffnen der Datei, oder die Datei weist ein ungültiges Format.|  
|E_PDB_FORMAT|Es wurde versucht, Zugriff auf eine Datei mit der ein veraltetes Format.|  
|E_PDB_INVALID_SIG|Signatur stimmt nicht überein.|  
|E_PDB_INVALID_AGE|Alter stimmt nicht überein.|  
|E_INVALIDARG|Ungültiger Parameter.|  
|E_UNEXPECTED|Die Datenquelle wurde bereits vorbereitet.|  
  
## <a name="remarks"></a>Hinweise  
 Eine PDB-Datei enthält sowohl die Signatur als auch die Age-Werte. Diese Werte werden in .exe oder .dll-Datei repliziert, die die PDB-Datei entspricht. Vor der Vorbereitung der Datenquelle, überprüft diese Methode an, dass die Signatur und das Alter des benannten PDB-Datei mit die angegebenen Werten übereinstimmen.  
  
 Verwenden Sie zum Laden einer PDB-Datei ohne Überprüfung der [idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) Methode.  
  
 Verwenden Sie für den Zugriff auf den Ladevorgang der Daten (durch einen Rückrufmechanismus bereit), die [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode.  
  
 Um eine PDB-Datei direkt aus dem Arbeitsspeicher zu laden, verwenden die [idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) Methode.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)



