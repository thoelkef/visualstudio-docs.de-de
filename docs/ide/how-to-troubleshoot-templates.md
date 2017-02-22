---
title: "Gewusst wie: Problembehandlung bei Vorlagen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio-Vorlagen, Problembehandlung"
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Problembehandlung bei Vorlagen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn eine Vorlage in der Entwicklungsumgebung nicht geladen werden kann, können Sie das Problem auf verschiedene Arten lokalisieren.  
  
## Überprüfen der VSTEMPLATE\-Datei  
 Wenn die VSTEMPLATE\-Datei in einer Vorlage nicht dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Vorlagenschema entspricht, wird die Vorlage möglicherweise nicht im Dialogfeld **Neues Projekt** angezeigt.  
  
#### So überprüfen Sie die VSTEMPLATE\-Datei  
  
1.  Suchen Sie die ZIP\-Datei, die die Vorlage enthält.  
  
2.  Extrahieren Sie die ZIP\-Datei.  
  
3.  Klicken Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im Menü **Datei** auf **Öffnen** und dann auf **Datei**.  
  
4.  Wählen Sie die VSTEMPLATE\-Datei für die Vorlage aus, und klicken Sie auf **Öffnen**.  
  
5.  Überprüfen Sie, ob der XML\-Code der VSTEMPLATE\-Datei dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Vorlagenschema entspricht.  Weitere Informationen zum VSTEMPLATE\-Schema finden Sie in der [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md).  
  
    > [!NOTE]
    >  Um beim Schreiben der VSTEMPLATE\-Datei IntelliSense\-Unterstützung zu erhalten, fügen Sie ein `xmlns`\-Attribut zum `VSTemplate`\-Element hinzu und weisen ihm den Wert http:\/\/schemas.microsoft.com\/developer\/vstemplate\/2005 zu.  
  
6.  Speichern und schließen Sie die VSTEMPLATE\-Datei.  
  
7.  Wählen Sie die in die Vorlage eingeschlossenen Dateien aus, und klicken Sie mit der rechten Maustaste. Wählen Sie **Senden an**, und klicken Sie auf **ZIP\-komprimierter Ordner**.  Die ausgewählten Dateien werden in einer ZIP\-Datei komprimiert.  
  
8.  Fügen Sie die neue ZIP\-Datei in dasselbe Verzeichnis ein, in dem sich die alte ZIP\-Datei befand.  
  
9. Löschen Sie die extrahierten Vorlagendateien und die alte ZIP\-Datei der Vorlage.  
  
## Überwachen des Ereignisprotokolls  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] protokolliert Fehler, die beim Verarbeiten der ZIP\-Dateien von Vorlagen auftreten.  Wenn die Vorlage nicht wie erwartet im Dialogfeld **Neues Projekt** angezeigt wird, können Sie das Problem mit der **Ereignisanzeige** beheben.  
  
#### So suchen Sie Vorlagenfehler in der Ereignisanzeige  
  
1.  Klicken Sie in Windows auf **Start** und **Systemsteuerung**, und doppelklicken Sie erst auf **Verwaltung** und dann auf **Ereignisanzeige**.  
  
2.  Klicken Sie im linken Bereich auf **Anwendung**.  
  
3.  Suchen Sie nach Ereignissen, die unter **Quelle** den Wert `Visual Studio - VsTemplate` aufweisen.  
  
4.  Doppelklicken Sie auf ein Vorlagenereignis, um den Fehler anzuzeigen.  
  
## Siehe auch  
 [Anpassen von Vorlagen](../ide/customizing-project-and-item-templates.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)