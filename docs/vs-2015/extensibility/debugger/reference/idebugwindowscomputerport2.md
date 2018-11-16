---
title: IDebugWindowsComputerPort2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d51769c39a7a6b3b98ed0e07e541b6563913e052
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763148"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ermöglicht das Abfragen von Informationen über den Zielcomputer.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugWindowsComputerPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von Port-Objekten, von der Sitzungs-Manager implementiert.  
  
## <a name="methods"></a>Methoden  
 Die folgende Tabelle zeigt die Methoden der `IDebugWindowsComputerPort2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Ruft Informationen über den Computer, auf denen der Debugger in ausgeführt wird.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

