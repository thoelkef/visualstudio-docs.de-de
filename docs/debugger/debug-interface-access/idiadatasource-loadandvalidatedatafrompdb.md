---
title: 'IDiaDataSource:: loadAndValidateDataFromPdb | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97afff946827c37ec2f84457016525377977dc8b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745001"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
Öffnet und überprüft, ob die Programm Datenbankdatei (PDB-Datei) mit den bereitgestellten Signatur Informationen übereinstimmt, und bereitet die PDB-Datei als debugdatenquelle vor.

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

in Der Pfad zur PDB-Datei.

`pcsig70`

in Die GUID-Signatur, die anhand der PDB-Datei Signatur überprüft werden soll. Nur PDB-Dateien in [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] und höher verfügen über GUID-Signaturen.

`sig`

in Die 32-Bit-Signatur, die anhand der PDB-Datei Signatur überprüft werden soll.

`age`

in Der zu überprüfende Alters Wert. Das Alter entspricht nicht notwendigerweise einem bekannten Uhrzeitwert. es wird verwendet, um zu bestimmen, ob eine PDB-Datei mit einer entsprechenden exe-Datei nicht synchronisiert ist.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. In der folgenden Tabelle sind die möglichen Rückgabewerte für diese Methode aufgeführt.

|Wert|Beschreibung|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Die Datei konnte nicht geöffnet werden, oder die Datei weist ein ungültiges Format auf.|
|E_PDB_FORMAT|Es wurde versucht, auf eine Datei mit einem veralteten Format zuzugreifen.|
|E_PDB_INVALID_SIG|Signatur stimmt nicht mit ab.|
|E_PDB_INVALID_AGE|Das Alter stimmt nicht mit.|
|E_INVALIDARG|Ungültiger Parameter.|
|E_UNEXPECTED|Die Datenquelle wurde bereits vorbereitet.|

## <a name="remarks"></a>Hinweise
Eine PDB-Datei enthält sowohl Signatur-als auch Alters Werte. Diese Werte werden in der exe-oder DLL-Datei repliziert, die mit der PDB-Datei übereinstimmt. Vor dem Vorbereiten der Datenquelle überprüft diese Methode, ob die Signatur und das Alter der benannten PDB-Datei mit den angegebenen Werten identisch sind.

Wenn Sie eine PDB-Datei ohne Validierung laden möchten, verwenden Sie die [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) -Methode.

Verwenden Sie die Methode [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) , um Zugriff auf den Daten Ladevorgang zu erhalten (über einen Rückrufmechanismus).

Verwenden Sie die [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) -Methode, um eine PDB-Datei direkt aus dem Arbeitsspeicher zu laden.

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
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
