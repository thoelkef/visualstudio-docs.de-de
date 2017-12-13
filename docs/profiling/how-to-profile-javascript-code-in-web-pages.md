---
title: "Vorgehensweise: Profilerstellung für JavaScript-Code in Webseiten | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e33605b75dfe80bf755081692bc8a4991def801
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2017
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Vorgehensweise: Profilerstellung für JavaScript-Code in Webseiten
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools können mithilfe der Instrumentierungsmethode für die Profilerstellung Leistungsdaten für JavaScript-Code sammeln, der in einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung, auf einer beliebigen Webseite oder in einer JavaScript-Anwendung ausgeführt wird.  
  
 **Anforderungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
-   Internet Explorer 8 oder höher.  
  
> [!WARNING]
>  Informationen zur Profilerstellung für JavaScript in UWP-Apps finden sie unter [JavaScript-Speicher](../profiling/javascript-memory.md) 
  
 Zum Erstellen einer Leistungssitzung können Sie den Profilerstellungs-Assistenten verwenden. Geben Sie die Instrumentationsmethode an, und wählen Sie dann im Dialogfeld "Eigenschaften" für die Leistungssitzung auf der Seite "Instrumentation" die Option für die Profilerstellung für JavaScript aus.  
  
 Wenn Sie die Profilerstellung für JavaScript angeben, erfolgt die Profilerstellung für den JavaScript-Code, der im Browser ausgeführt wird, und den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Code, der auf dem Server ausgeführt wird.  
  
-   Bei einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Webanwendung erfolgt die Profilerstellung für den JavaScript-Code, der im Browser ausgeführt wird, und den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Code, der auf dem Server ausgeführt wird.  
  
-   Bei einer beliebigen Webseite erfolgt die Profilerstellung für den JavaScript-Code, der im Browser ausgeführt wird.  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>So aktivieren Sie die Profilerstellung für JavaScript in einem ASP.NET-Webanwendungsprojekt  
  
1.  Öffnen Sie in [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]das [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Webprojekt.  
  
2.  Klicken Sie im Menü **Analyse** auf **Leistungs-Assistenten starten**.  
  
3.  Geben Sie auf der ersten Seite des Leistungs-Assistenten die Profilerstellungsmethode **Instrumentation** an, und klicken Sie dann auf **Weiter**.  
  
4.  Stellen Sie auf der zweiten Seite des Assistenten sicher, dass das aktuelle Projekt in der Liste der Ziele ausgewählt ist, und klicken Sie dann auf **Weiter.**  
  
5.  Aktivieren Sie auf der dritten Seite des Assistenten das Kontrollkästchen **Profilerstellung für JavaScript** , und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie auf der vierten Seite des Assistenten auf **Fertig stellen** , um die Webanwendung im Browser zu starten.  
  
7.  Verwenden Sie die Funktionen, für die eine Profilerstellung erfolgen soll.  
  
8.  Wenn Sie die Profilerstellungssitzung beenden möchten, schließen Sie den Browser.  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>So aktivieren Sie die Profilerstellung für JavaScript auf einzelnen Webseiten oder in JavaScript-Anwendungen  
  
1.  Öffnen Sie [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)].  
  
2.  Klicken Sie im Menü **Analyse** auf **Leistungs-Assistenten starten**.  
  
3.  Geben Sie auf der ersten Seite des Leistungs-Assistenten die Profilerstellungsmethode **Instrumentation** an, und klicken Sie dann auf **Weiter**.  
  
4.  Klicken Sie auf der zweiten Seite des Assistenten auf eine ASP NET- oder avaScript-Anwendung, und klicken Sie dann auf **Weiter.**  
  
5.  Führen Sie auf der vierten Seite des Assistenten folgende Schritte aus:  
  
    1.  Geben Sie im Feld **URL oder Pfad für die Ausführung der Anwendung** die URL der Seite an.  
  
    2.  Aktivieren Sie das Kontrollkästchen **Profilerstellung für JavaScript** , und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie auf der vierten Seite des Assistenten auf **Fertig stellen** , um die Webseite im Browser zu starten.  
  
7.  Verwenden Sie die Funktionen, für die eine Profilerstellung erfolgen soll.  
  
8.  Wenn Sie die Profilerstellungssitzung beenden möchten, schließen Sie den Browser.