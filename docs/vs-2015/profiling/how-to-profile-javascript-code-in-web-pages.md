---
title: 'Vorgehensweise: Profilerstellung für JavaScript-Code in Webseiten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f838974292a16a9aeaea11362848b06f5abe982
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60048514"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Vorgehensweise: Profilerstellung für JavaScript-Code in Webseiten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Profilerstellungstools können mithilfe der Instrumentationsmethode für die Profilerstellung Leistungsdaten für JavaScript-Code sammeln, der in einer [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Webanwendung, auf einer beliebigen Webseite oder in einer JavaScript-Anwendung ausgeführt wird.  
  
 **Anforderungen**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
- Internet Explorer 8 oder höher.  
  
> [!WARNING]
>  Die Profilerstellung für JavaScript in Windows Store-Apps ist in den folgenden Themen beschrieben:  
> 
> - [JavaScript-Funktionstiming](http://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03) [JavaScript-Funktionstiming auf einem Remotegerät](http://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
>   - [Analysieren von JavaScript-Funktionstimingdaten](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
>   - 
  
 Zum Erstellen einer Leistungssitzung können Sie den Profilerstellungs-Assistenten verwenden. Geben Sie die Instrumentationsmethode an, und wählen Sie dann im Dialogfeld "Eigenschaften" für die Leistungssitzung auf der Seite "Instrumentation" die Option für die Profilerstellung für JavaScript aus.  
  
 Wenn Sie die Profilerstellung für JavaScript angeben, erfolgt die Profilerstellung für den JavaScript-Code, der im Browser ausgeführt wird, und den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Code, der auf dem Server ausgeführt wird.  
  
- Bei einer [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendung erfolgt die Profilerstellung für den JavaScript-Code, der im Browser ausgeführt wird, und den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Code, der auf dem Server ausgeführt wird.  
  
- Bei einer beliebigen Webseite erfolgt die Profilerstellung für den JavaScript-Code, der im Browser ausgeführt wird.  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>So aktivieren Sie die Profilerstellung für JavaScript in einem ASP.NET-Webanwendungsprojekt  
  
1. Öffnen Sie in [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] das Webprojekt [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
2. Klicken Sie im Menü **Analyse** auf **Leistungs-Assistenten starten**.  
  
3. Geben Sie auf der ersten Seite des Leistungs-Assistenten die Profilerstellungsmethode **Instrumentation** an, und klicken Sie dann auf **Weiter**.  
  
4. Stellen Sie auf der zweiten Seite des Assistenten sicher, dass das aktuelle Projekt in der Liste der Ziele ausgewählt ist, und klicken Sie dann auf **Weiter.**  
  
5. Aktivieren Sie auf der dritten Seite des Assistenten das Kontrollkästchen **Profilerstellung für JavaScript** , und klicken Sie dann auf **Weiter**.  
  
6. Klicken Sie auf der vierten Seite des Assistenten auf **Fertig stellen** , um die Webanwendung im Browser zu starten.  
  
7. Verwenden Sie die Funktionen, für die eine Profilerstellung erfolgen soll.  
  
8. Wenn Sie die Profilerstellungssitzung beenden möchten, schließen Sie den Browser.  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>So aktivieren Sie die Profilerstellung für JavaScript auf einzelnen Webseiten oder in JavaScript-Anwendungen  
  
1. Öffnen Sie [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)].  
  
2. Klicken Sie im Menü **Analyse** auf **Leistungs-Assistenten starten**.  
  
3. Geben Sie auf der ersten Seite des Leistungs-Assistenten die Profilerstellungsmethode **Instrumentation** an, und klicken Sie dann auf **Weiter**.  
  
4. Klicken Sie auf der zweiten Seite des Assistenten auf eine ASP NET- oder avaScript-Anwendung, und klicken Sie dann auf **Weiter.**  
  
5. Führen Sie auf der vierten Seite des Assistenten folgende Schritte aus:  
  
    1. Geben Sie im Feld **URL oder Pfad für die Ausführung der Anwendung** die URL der Seite an.  
  
    2. Aktivieren Sie das Kontrollkästchen **Profilerstellung für JavaScript** , und klicken Sie dann auf **Weiter**.  
  
6. Klicken Sie auf der vierten Seite des Assistenten auf **Fertig stellen** , um die Webseite im Browser zu starten.  
  
7. Verwenden Sie die Funktionen, für die eine Profilerstellung erfolgen soll.  
  
8. Wenn Sie die Profilerstellungssitzung beenden möchten, schließen Sie den Browser.
