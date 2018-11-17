---
title: 'Vorgehensweise: Angeben der .NET Framework-Laufzeit | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c62b70816ac17789a4aa236e5abcca6832f7359
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749297"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Vorgehensweise: Angeben der .NET Framework-Laufzeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit der Veröffentlichung von [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] können Anwendungen mit Modulen zusammengesetzt sein, die mit verschiedenen Versionen der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Laufzeit erstellt wurden. Standardmäßig erstellen die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools für die erste Laufzeit, die von der Anwendung geladen wird, ein Profil. Sie können die Laufzeit zur Profilerstellung angeben, wenn Sie eine Anwendung mit dem Profiler starten, und wenn Sie den Profiler an eine bereits ausgeführte Anwendung anfügen.  
  
 **Anforderungen**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>So geben Sie die .NET Framework-Laufzeit, für die ein Profil erstellt werden soll, beim Starten einer Anwendung über den Profiler an  
  
1.  Klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf die Leistungssitzung, nun auf **Eigenschaften** und anschließend auf **Erweitert**.  
  
     Das Listenfeld **Ziel-CLR-Version** zeigt **Automatisch** und die Versionen der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Laufzeit an, die auf dem Computer installiert sind.  
  
2.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Klicken Sie auf die Version der CLR, für die Sie ein Profil erstellen möchten.  
  
    -   Klicken Sie auf **Automatisch**, um für die erste Version, die von der Anwendung geladen wird, ein Profil zu erstellen.  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>So geben Sie die .NET Framework-Laufzeit, für die ein Profil erstellt werden soll, beim Anfügen des Profilers an eine Anwendung an  
  
1.  Zeigen Sie m Menü Analysieren auf Profiler und klicken Sie anschließend auf Anfügen/Trennen.  
  
2.  Klicken Sie im Dialogfeld „Profiler an Prozess anfügen“ auf den Prozess, für den Sie ein Profil erstellen möchten.  
  
     Das Listenfeld **Ziel-CLR-Version** zeigt **Automatisch** und die Versionen der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Laufzeit an, die auf dem Computer installiert sind.  
  
3.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Klicken Sie auf die Version der CLR, für die Sie ein Profil erstellen möchten.  
  
    -   Klicken Sie auf **Automatisch**, um für die Version ein Profil zu erstellen, die geladen wird, wenn der Profiler an die Anwendung angefügt wird.



