---
title: Datei Status Code Enumerator | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b3415440c80fcaa88edbecee924a118f82a9dd99
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128167"
---
# <a name="file-status-code-enumerator"></a>Code-Status-Datei-Enumerator
Die `SccStatus` Enumerator enthält benannte Konstante Werte, die den Zustand einer Datei in das Quellcodeverwaltungssystem angeben. Diese Enumeration wird verwendet, durch die [SccQueryInfo](../extensibility/sccqueryinfo-function.md) und `POPLISTFUNC` Rückruffunktion (finden Sie unter [POPLISTFUNC](../extensibility/poplistfunc.md) Einzelheiten).  
  
## <a name="syntax"></a>Syntax  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## <a name="members"></a>Member  
 SCC_STATUS_INVALID  
 Status konnte nicht abgerufen werden. verlassen Sie sich nicht darauf.  
  
 SCC_STATUS_NOTCONTROLLED  
 Datei ist nicht in der quellcodeverwaltung.  
  
 SCC_STATUS_CONTROLLED  
 Datei wird in die quellcodeverwaltung.  
  
 SCC_STATUS_CHECKEDOUT  
 Ausgecheckt, vom aktuellen Benutzer auf dem lokalen Datenträger.  
  
 SCC_STATUS_OUTOTHER  
 Datei wird von einem anderen Benutzer ausgecheckt.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 Datei ist exklusiv ausgecheckt.  
  
 SCC_STATUS_OUTMULTIPLE  
 Datei wird von mehr als einem Benutzer ausgecheckt.  
  
 SCC_STATUS_OUTOFDATE  
 Die Datei ist nicht die aktuellste Version.  
  
 SCC_STATUS_DELETED  
 Datei wurde aus dem Projekt gelöscht.  
  
 SCC_STATUS_LOCKED  
 Datei ist gesperrt. keine weitere Versionen zulässig.  
  
 SCC_STATUS_MERGED  
 Datei zusammengeführt, aber noch nicht behoben und überprüft wurde.  
  
 SCC_STATUS_SHARED  
 Datei wird zwischen Projekten gemeinsam genutzt.  
  
 SCC_STATUS_PINNED  
 Um eine explizite Version freigegeben wird.  
  
 SCC_STATUS_MODIFIED  
 Datei wurde geändert/unterteilt/verletzt.  
  
 SCC_STATUS_OUTBYUSER  
 Datei wird vom aktuellen Benutzer ausgecheckt.  
  
 SCC_STATUS_NOMERGE  
 Datei kann nie mit zusammengeführt werden und muss nicht gespeichert werden, bevor Sie einen GET-Befehl.  
  
 SCC_STATUS_RESERVED_1  
 Für die interne Verwendung vorgesehen.  
  
 SCC_STATUS_RESERVED_2  
 Für die interne Verwendung vorgesehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen-Steuerelement-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)