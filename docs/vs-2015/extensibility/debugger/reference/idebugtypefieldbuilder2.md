---
title: IDebugTypeFieldBuilder2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 96241026afff71c061abcfae3547d25cc2166902
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152877"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erweitert die **IDebugTypeFieldBuilder** Arraytypen erstellen können.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder  
```  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle kann von der symbolanbieter abgerufen werden.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den Methoden für die [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) Schnittstelle, die diese Schnittstelle implementiert, die folgende Methode:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Erstellt ein Array des angegebenen Typs und der Größe.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
