---
title: COMPUTER_INFO | Microsoft-Dokumentation
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
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f96d42936f62b7724629127a638d2ea534d3b6f4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883041"
---
# <a name="computerinfo"></a>COMPUTER_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beschreibt, den Computer, auf dem der Debugger ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagCOMPUTER_INFO  
{  
    WORD wProcessorArchitecture;  
    WORD wSuiteMask;  
    DWORD dwOperatingSystemVersion;  
} COMPUTER_INFO;  
```  
  
```csharp  
public struct COMPUTER_INFO  
{  
    public ushort wProcessorArchitecture;  
    public ushort wSuiteMask;  
    public uint dwOperatingSystemVersion;  
}  
```  
  
## <a name="terms"></a>Begriffe  
 wProcessorArchitecture  
 Gibt die Architektur des Mikroprozessors an.  
  
 wSuiteMask  
 Identifiziert die Suite-Maske.  
  
 dwOperatingSystemVersion  
 Betriebssystem-Versionsnummer.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zurückgegeben, durch die [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)

