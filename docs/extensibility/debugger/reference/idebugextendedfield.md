---
title: IDebugExtendedField | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7702f7acded3f69f2e6bb1aada8fbe2935c9f3a5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034024"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
Erweitert die Typen von Feldern, die zur Unterstützung von Generika mit verwaltetem Code verfügbar sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugExtendedField : IDebugField  
```  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den Methoden für die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle, die diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Ruft die Art des angegebenen erweiterten Feldeigenschaften ab.|  
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Bestimmt, ob das Feld einen geschlossenen Typ darstellt.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll