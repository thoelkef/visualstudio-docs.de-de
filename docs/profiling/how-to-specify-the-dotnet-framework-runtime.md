---
title: "Gewusst wie: Angeben der .NET Framework-Laufzeit f&#252;r die Profilerstellung in parallelen Szenarios | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilerstellungstools, .NET Framework-Versionen"
  - ".NET Framework-Versionen,Profilerstellung"
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Angeben der .NET Framework-Laufzeit f&#252;r die Profilerstellung in parallelen Szenarios
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit der [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)]\-Version können Anwendungen aus Modulen zusammengesetzt werden, die mit verschiedenen Versionen der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Laufzeit erstellt wurden.  Standardmäßig wird von den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools ein Profil für die erste Laufzeit erstellt, die von der Anwendung geladen wird.  Sie können die Laufzeit, für die ein Profil erstellt werden soll, beim Starten einer Anwendung über den Profiler oder beim Anfügen des Profilers an eine aktive Anwendung angeben.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### So geben Sie die .NET Framework\-Laufzeit, für die ein Profil erstellt werden soll, beim Starten einer Anwendung über den Profiler an  
  
1.  Klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf **Eigenschaften** und dann auf **Erweitert**.  
  
     Das Listenfeld **Ziel\-CLR\-Version** zeigt **Automatisch** und die Versionen der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Laufzeit an, die auf dem Computer installiert sind.  
  
2.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Klicken Sie auf die CLR\-Version, für die ein Profil erstellt werden soll.  
  
    -   Klicken Sie auf **Automatisch**, um ein Profil für die erste Version zu erstellen, die von der Anwendung geladen wird.  
  
### So geben Sie die .NET Framework\-Laufzeit, für die ein Profil erstellt werden soll, beim Anfügen des Profilers an eine Anwendung an  
  
1.  Zeigen Sie im Menü Analyse auf Profiler, und klicken Sie dann auf Anfügen\/Trennen.  
  
2.  Klicken Sie im Dialogfeld "Profiler an Prozess anfügen" auf den Prozess, für den ein Profil erstellt werden soll.  
  
     Das Listenfeld **Ziel\-CLR\-Version** zeigt **Automatisch** und die Versionen der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Laufzeit an, die auf dem Computer installiert sind.  
  
3.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Klicken Sie auf die CLR\-Version, für die ein Profil erstellt werden soll.  
  
    -   Klicken Sie auf **Automatisch**, um ein Profil für die Version zu erstellen, die beim Anfügen des Profilers an die Anwendung geladen wird.