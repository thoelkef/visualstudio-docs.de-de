---
title: 'Idiadatasource:: Loadandvalidatedatafrompdb | Microsoft-Dokumentation'
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
ms.openlocfilehash: 5426e27d7b100c42cd571935b1634d6dbd6e990f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626140"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
Wird geöffnet und überprüft, ob die Programmdatenbankdatei (.pdb) der bereitgestellten Signaturinformationen entspricht, und bereitet die PDB-Datei als Datenquelle Debuggen.

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

[in] Die GUID-Signatur der Signatur der PDB-Datei überprüft werden soll. Nur PDB-Dateien im [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] und später GUID-Signaturen aufweisen.

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

## <a name="remarks"></a>Anmerkungen
Eine PDB-Datei enthält sowohl die Signatur als auch die Age-Werte. Diese Werte werden in .exe oder .dll-Datei repliziert, die die PDB-Datei entspricht. Vor der Vorbereitung der Datenquelle, überprüft diese Methode an, dass die Signatur und das Alter des benannten PDB-Datei mit die angegebenen Werten übereinstimmen.

Verwenden Sie zum Laden einer PDB-Datei ohne Überprüfung der [idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) Methode.

Verwenden Sie für den Zugriff auf den Ladevorgang der Daten (durch einen Rückrufmechanismus bereit), die [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode.

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
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
