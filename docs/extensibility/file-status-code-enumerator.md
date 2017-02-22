---
title: "Dateienumerator Status-Code | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "benannte Konstanten SccStatus-enumerator"
  - "Source Control-Plug-ins Datei Status-enumeration"
  - "SccStatus-enumerator"
  - "Dateienumerator Status-code"
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Dateienumerator Status-Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die `SccStatus` Enumerator enthält benannte Konstante Werte, die den Status einer Datei im Quellcode\-Verwaltungssystem angeben. Diese Enumeration wird verwendet, indem Sie die [SccQueryInfo](../extensibility/sccqueryinfo-function.md) und die `POPLISTFUNC` Callback\-Funktion \(finden Sie unter [POPLISTFUNC](../extensibility/poplistfunc.md) Details\).  
  
## Syntax  
  
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
  
## Mitglieder  
 SCC\_STATUS\_INVALID  
 Status konnte nicht abgerufen werden. verlassen Sie sich nicht darauf.  
  
 SCC\_STATUS\_NOTCONTROLLED  
 Datei ist nicht in einem Quellcodeverwaltungsprojekt.  
  
 SCC\_STATUS\_CONTROLLED  
 Datei wird unter Versionskontrolle.  
  
 SCC\_STATUS\_CHECKEDOUT  
 Ausgecheckt, vom aktuellen Benutzer auf dem lokalen Datenträger.  
  
 SCC\_STATUS\_OUTOTHER  
 Datei wird von einem anderen Benutzer ausgecheckt.  
  
 SCC\_STATUS\_OUTEXCLUSIVE  
 Datei ist exklusiv ausgecheckt.  
  
 SCC\_STATUS\_OUTMULTIPLE  
 Datei wird von mehr als einem Benutzer ausgecheckt.  
  
 SCC\_STATUS\_OUTOFDATE  
 Die Datei ist nicht die aktuellste Version.  
  
 SCC\_STATUS\_DELETED  
 Datei wurde aus dem Projekt gelöscht.  
  
 SCC\_STATUS\_LOCKED  
 Datei ist gesperrt. keine weitere Versionen zulässig.  
  
 SCC\_STATUS\_MERGED  
 Datei wurde zusammengeführt, aber noch nicht behoben und überprüft.  
  
 SCC\_STATUS\_SHARED  
 Datei wird von Projekten gemeinsam verwendet.  
  
 SCC\_STATUS\_PINNED  
 Eine bestimmte Version freigegeben wird.  
  
 SCC\_STATUS\_MODIFIED  
 Datei wurde geändert\/fehlerhafte\/verletzt.  
  
 SCC\_STATUS\_OUTBYUSER  
 Datei wird vom aktuellen Benutzer ausgecheckt.  
  
 SCC\_STATUS\_NOMERGE  
 Datei kann nicht mit zusammengeführt werden und muss nicht gespeichert werden, bevor Sie eine GET.  
  
 SCC\_STATUS\_RESERVED\_1  
 Für die interne Verwendung vorgesehen.  
  
 SCC\_STATUS\_RESERVED\_2  
 Für die interne Verwendung vorgesehen.  
  
## Siehe auch  
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)