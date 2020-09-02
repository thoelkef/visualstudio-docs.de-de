---
title: Datei Status Code-Enumerator | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1b6e74caa9eedd42e25339d62f5837ccfe82d001
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204376"
---
# <a name="file-status-code-enumerator"></a>Dateistatuscode-Enumerator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der `SccStatus` Enumerator enthält benannte Konstante Werte, die den Zustand einer Datei im Quell Code Verwaltungssystem angeben. Diese Enumeration wird von der [sccqueryinfo](../extensibility/sccqueryinfo-function.md) -Funktion und der `POPLISTFUNC` Callback-Funktion verwendet (Weitere Informationen finden Sie unter [poplistfunc](../extensibility/poplistfunc.md) ).  
  
## <a name="syntax"></a>Syntax  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## <a name="members"></a>Member  
 SCC_STATUS_INVALID  
 Der Status konnte nicht abgerufen werden. verlassen Sie sich nicht darauf.  
  
 SCC_STATUS_NOTCONTROLLED  
 Die Datei befindet sich nicht unter Quell Code Verwaltung.  
  
 SCC_STATUS_CONTROLLED  
 Die Datei befindet sich unter Quell Code Verwaltung.  
  
 SCC_STATUS_CHECKEDOUT  
 Vom aktuellen Benutzer auf dem lokalen Datenträger ausgecheckt.  
  
 SCC_STATUS_OUTOTHER  
 Die Datei wird von einem anderen Benutzer ausgecheckt.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 Die Datei ist exklusiv ausgecheckt.  
  
 SCC_STATUS_OUTMULTIPLE  
 Die Datei wird von mehr als einem Benutzer ausgecheckt.  
  
 SCC_STATUS_OUTOFDATE  
 Die Datei ist nicht die aktuellste.  
  
 SCC_STATUS_DELETED  
 Die Datei wurde aus dem Projekt gelöscht.  
  
 SCC_STATUS_LOCKED  
 Die Datei ist gesperrt. Es sind keine weiteren Versionen zulässig.  
  
 SCC_STATUS_MERGED  
 Die Datei wurde zusammengeführt, aber noch nicht korrigiert/überprüft.  
  
 SCC_STATUS_SHARED  
 Die Datei wird von Projekten gemeinsam verwendet.  
  
 SCC_STATUS_PINNED  
 Die Datei wird für eine explizite Version freigegeben.  
  
 SCC_STATUS_MODIFIED  
 Die Datei wurde geändert/beschädigt/verletzt.  
  
 SCC_STATUS_OUTBYUSER  
 Die Datei wird vom aktuellen Benutzer ausgecheckt.  
  
 SCC_STATUS_NOMERGE  
 Die Datei kann nie zusammengeführt werden und muss nicht vor dem Get-Zeitpunkt gespeichert werden.  
  
 SCC_STATUS_RESERVED_1  
 Für die interne Verwendung reserviert.  
  
 SCC_STATUS_RESERVED_2  
 Für die interne Verwendung reserviert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [Sccqueryinfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)
