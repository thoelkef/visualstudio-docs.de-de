---
title: "Gewusst wie: Profilerstellung f&#252;r JavaScript-Code (ECMA) in Webseiten | Microsoft Docs"
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
  - "JavaScript-Leistungsprofilerstellung"
  - "Profilerstellungstools, JavaScript"
  - "Website-Leistungsprofilerstellung"
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Profilerstellung f&#252;r JavaScript-Code (ECMA) in Webseiten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools können mithilfe der Instrumentationsmethode für die Profilerstellung Leistungsdaten für JavaScript\-Code sammeln, der in einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendung, auf einer beliebigen Webseite oder in einer JavaScript\-Anwendung ausgeführt wird.  
  
 **Anforderungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
-   Internet Explorer 8 oder höher.  
  
> [!WARNING]
>  Die Profilerstellung für JavaScript in Windows Store\-Apps ist in den folgenden Themen beschrieben:  
>   
>  -   [Sammeln von JavaScript\-Funktionstimingdaten auf einem lokalen Computer](../Topic/JavaScript%20Function%20Timing.md) [Sammeln von JavaScript\-Funktionstimingdaten auf einem Remotegerät](../Topic/JavaScript%20Function%20Timing%20on%20a%20Remote%20Device.md)  
> -   [Analysieren von JavaScript\-Funktionstimingdaten](../Topic/Analyze%20JavaScript%20Function%20Timing%20data.md)  
> -  
  
 Zum Erstellen einer Leistungssitzung können Sie den Profilerstellungs\-Assistenten verwenden. Geben Sie die Instrumentationsmethode an, und wählen Sie dann im Dialogfeld "Eigenschaften" für die Leistungssitzung auf der Seite "Instrumentation" die Option für die Profilerstellung für JavaScript aus.  
  
 Wenn Sie die Profilerstellung für JavaScript angeben, erfolgt die Profilerstellung für den JavaScript\-Code, der im Browser ausgeführt wird, und den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Code, der auf dem Server ausgeführt wird.  
  
-   Bei einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendung erfolgt die Profilerstellung für den JavaScript\-Code, der im Browser ausgeführt wird, und den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Code, der auf dem Server ausgeführt wird.  
  
-   Bei einer beliebigen Webseite erfolgt die Profilerstellung für den JavaScript\-Code, der im Browser ausgeführt wird.  
  
### So aktivieren Sie die Profilerstellung für JavaScript in einem ASP.NET\-Webanwendungsprojekt  
  
1.  Öffnen Sie in [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] das [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webprojekt.  
  
2.  Klicken Sie im Menü **Analyse** auf **Leistungs\-Assistenten starten**.  
  
3.  Geben Sie auf der ersten Seite des Leistungs\-Assistenten die Profilerstellungsmethode **Instrumentation** an, und klicken Sie dann auf **Weiter**.  
  
4.  Stellen Sie auf der zweiten Seite des Assistenten sicher, dass das aktuelle Projekt in der Liste der Ziele ausgewählt ist, und klicken Sie dann auf **Weiter.**  
  
5.  Aktivieren Sie auf der dritten Seite des Assistenten das Kontrollkästchen **Profilerstellung für JavaScript**, und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie auf der vierten Seite des Assistenten auf **Fertig stellen**, um die Webanwendung im Browser zu starten.  
  
7.  Verwenden Sie die Funktionen, für die eine Profilerstellung erfolgen soll.  
  
8.  Wenn Sie die Profilerstellungssitzung beenden möchten, schließen Sie den Browser.  
  
### So aktivieren Sie die Profilerstellung für JavaScript auf einzelnen Webseiten oder in JavaScript\-Anwendungen  
  
1.  Öffnen Sie [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)].  
  
2.  Klicken Sie im Menü **Analyse** auf **Leistungs\-Assistenten starten**.  
  
3.  Geben Sie auf der ersten Seite des Leistungs\-Assistenten die Profilerstellungsmethode **Instrumentation** an, und klicken Sie dann auf **Weiter**.  
  
4.  Klicken Sie auf der zweiten Seite des Assistenten auf eine ASP NET\- oder avaScript\-Anwendung, und klicken Sie dann auf **Weiter.**  
  
5.  Führen Sie auf der vierten Seite des Assistenten folgende Schritte aus:  
  
    1.  Geben Sie im Feld **URL oder Pfad für die Ausführung der Anwendung** die URL der Seite an.  
  
    2.  Aktivieren Sie das Kontrollkästchen **Profilerstellung für JavaScript**, und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie auf der vierten Seite des Assistenten auf **Fertig stellen**, um die Webseite im Browser zu starten.  
  
7.  Verwenden Sie die Funktionen, für die eine Profilerstellung erfolgen soll.  
  
8.  Wenn Sie die Profilerstellungssitzung beenden möchten, schließen Sie den Browser.