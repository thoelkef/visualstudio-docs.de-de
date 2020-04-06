---
title: IDebugProperty2::GetExtendedInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34d6cd880ccae520bf000ad01b52223857f4f10f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721486"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Ruft erweiterte Informationen für die Eigenschaft ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetExtendedInfo ( 
   REFGUID* guidExtendedInfo,
   VARIANT* pExtendedInfo
);
```

```csharp
int GetExtendedInfo ( 
   ref Guid guidExtendedInfo,
   out object pExtendedInfo
);
```

## <a name="parameters"></a>Parameter
`guidExtendedInfo`\
[in] GUID, die den Typ der erweiterten Informationen bestimmt, die abgerufen werden sollen. Einzelheiten finden Sie in den Hinweisen.

`pExtendedInfo`\
[out] Gibt `VARIANT` ein (C++) oder Objekt (C') zurück, das zum Abrufen der erweiterten Eigenschafteninformationen verwendet werden kann. Dieser Parameter kann z. `IUnknown` B. eine Schnittstelle zurückgeben, die für eine [IDebugDocumentText2-Schnittstelle](../../../extensibility/debugger/reference/idebugdocumenttext2.md) abgefragt werden kann. Einzelheiten finden Sie in den Hinweisen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird Fehlercode zurückgegeben. Gibt `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` zurück, wenn keine erweiterten Informationen abgerufen werden sollen.

## <a name="remarks"></a>Bemerkungen
 Diese Methode ist zum Abrufen von Informationen vorhanden, die nicht zum Abrufen durch Aufrufen der [GetPropertyInfo-Methode](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) geeignet sind.

 Die folgenden GUIDs werden in der Regel von dieser Methode erkannt (die GUID-Werte werden für C- angegeben, da der Name in keiner Assembly verfügbar ist). Für den internen Gebrauch können zusätzliche GUIDs erstellt werden.

|name|GUID|BESCHREIBUNG|
|----------|----------|-----------------|
|guidDokument|3f98de84-fee9-11d0-b47f-00a0244a1dd2|Gibt `IUnknown` eine Schnittstelle an das Dokument zurück. In der Regel kann die [IDebugDocumentText2-Schnittstelle](../../../extensibility/debugger/reference/idebugdocumenttext2.md) über diese `IUnknown` Schnittstelle abgerufen werden.|
|guidCodeContext|E2fc65e-56ce-11d1-b528-00aax004a8797|Gibt `IUnknown` eine Schnittstelle an den Dokumentkontext zurück. In der Regel kann die [IDebugDocumentContext2-Schnittstelle](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) über diese `IUnknown` Schnittstelle abgerufen werden.|
|guidCustomViewerUnterstützt|D9c9da31-ffbe-4eeb-9186-23121e3c088c|Gibt eine Zeichenfolge zurück, die die CLSID eines benutzerdefinierten Viewers enthält, die in der Regel von einem Ausdrucksevaluator implementiert wird.|
|guidExtendedInfoSlot|6df235ad-82c6-4292-9c97-7389770bc42f|Gibt eine 32-Bit-Nummer zurück, die die gewünschte Steckplatznummer darstellt, wenn diese Eigenschaft eine lokale Adresse für verwalteten Code darstellt.|
|guidExtendedInfoSignature|B5fb6d46-f805-417f-96a3-8ba737073ffd|Gibt eine Zeichenfolge zurück, die die Signatur der Variablen enthält, die dem Eigenschaftsobjekt zugeordnet ist.|

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
