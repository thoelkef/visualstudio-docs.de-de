---
title: IDebugNoSymbolsEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1ea18b3799a73aa902d61a56669aaae1034ea8c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043335"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Signalisiert dem [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugger-Benutzeroberfläche auf den Benutzer zu warnen, dass die Symbole für die gestartete ausführbare Datei nicht gefunden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Von der Debug-Engines implementiert und von der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugger-Benutzeroberfläche.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll