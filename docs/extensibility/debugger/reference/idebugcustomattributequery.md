---
title: Idebugcustomattributequery | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 598db5ad711c8b61339e188311c1a437a24d013c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732609"
---
# <a name="idebugcustomattributequery"></a>IDebugCustomAttributeQuery
Stellt eine Abfrage für benutzerdefinierte Attribute für eine Methode oder einen Typ dar.

## <a name="syntax"></a>Syntax

```
IDebugCustomAttributeQuery : IUnknown
```

## <a name="methods"></a>Methoden
 Diese Schnittstelle implementiert die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|Ruft ein benutzerdefiniertes Attribut ab, dessen Name angegeben ist.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|Bestimmt, dass das angegebene benutzerdefinierte Attribut definiert ist.|

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
