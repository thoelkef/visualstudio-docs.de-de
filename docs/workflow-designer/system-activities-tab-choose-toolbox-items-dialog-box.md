---
title: "System.Activities (Registerkarte), Toolboxelemente ausw&#228;hlen (Dialogfeld) | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS"
  - "VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS"
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# System.Activities (Registerkarte), Toolboxelemente ausw&#228;hlen (Dialogfeld)
Diese Registerkarte des Dialogfelds **Toolboxelemente auswählen** enthält eine Liste der für Sie verfügbaren [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]\-Aktivitäten, Vorlagen und Elemente.Um diese Liste anzuzeigen, wählen Sie zunächst im Menü **Extras** die Option **Toolboxelemente auswählen** aus oder klicken Sie mit der rechten Maustaste auf **Toolbox** und wählen Sie **Elemente auswählen**, um das Dialogfeld **Toolboxelemente auswählen** anzuzeigen. Wählen Sie anschließend die Registerkarte **System.Activities** aus.Voreingestellt enthält die Liste Workflowaktivitäten aus den Assemblys System.Activities, System.ServiceModel.Activities und System.Activities.Core.Presentation. Allerdings werden nur die vom System bereitgestellten Aktivitäten und die durch andere Assemblys hinzugefügten Aktivitäten, die in der **Toolbox** angezeigte werden, standardmäßig markiert.Kürzlich hinzugefügte Aktivitäten werden automatisch markiert und in der **Toolbox** angezeigt, wenn Sie im Dialogfeld auf **OK** klicken.Diese Elemente werden in der **Toolbox** in einer neuen Kategorie angezeigt, die dem Namespace entspricht, in dem sich die Aktivität\/Element\/Vorlage befindet.  
  
> [!WARNING]
>  Wenn Sie versuchen, eine Assembly hinzuzufügen, die keine Workflowaktivitäten enthält, wird ein Dialogfeld mit einer Fehlermeldung angezeigt, die besagt, dass die Assembly keine Aktivitäten enthält.  
  
 Dieses Dialogfeld ist nicht auf das Projekt bezogen, und daher wird die Registerkarte **System.Activities** auch in einem eigenständigen XAML\-Projekt oder einem anderen Projekttyp als Workflow weiterhin angezeigt.  
  
 Die Filterung wird auf jeder Registerkarte ausgeführt.Dies bedeutet, dass es nicht möglich ist, Workflowaktivitäten über die Registerkarte **.NET\-Komponente** hinzuzufügen.Sie müssen über die Registerkarte **System.Activities** hinzugefügt werden.  
  
 Sie können alle Elemente deaktivieren, die nicht in der **Toolbox** auf dieser Dialogfeldregisterkarte angezeigt werden sollen. Stattdessen können Sie auch die Kontextmenüoption **Löschen** in der **Toolbox** verwenden. Durch Entfernen des Verweises auf die Assembly wird das Element nicht aus der **Toolbox** entfernt.  
  
 Durch Ziehen und Ablegen im Designer wird die Aktivität instanziiert und die Assembly, die das Element enthält, automatisch der Liste von Assemblys hinzugefügt, auf die verwiesen wird.Außerdem gilt, wenn die Aktivität auf eine Assembly C verweist, wird C nicht der Liste von Assemblys, auf die verwiesen wird, hinzugefügt.Assembly C muss im globalen Assemblycache \(GAC\) oder im selben Verzeichnis wie Aktivität B enthalten sein.Im Fall eines eigenständigen Projekts muss die Assembly im GAC oder den Überprüfungspfaden von VS vorhanden sein.Nur dann können Sie die Aktivität auf die Workflow\-Designer\-Oberfläche ziehen und dort ablegen.  
  
 **Toolbox**\-Einstellungen werden standardmäßig als Benutzeroptionen gespeichert. Wenn Sie die **Toolbox** das nächste Mal öffnen, wird daher die benutzerdefinierte Liste von Workflowaktivitäten angezeigt.Wenn Sie der **Toolbox** bestimmte Elemente Ihrer Domäne über das Dialogfeld **Toolboxelemente auswählen** hinzugefügt haben, werden diese Elemente deswegen auch dann weiterhin angezeigt, wenn Sie mit einer Konsolenanwendung für Workflows arbeiten.Wenn diese Elemente nicht mehr angezeigt werden sollen, müssen Sie sie mithilfe des Kontextmenüs löschen oder wie oben beschrieben über das Dialogfeld **Toolboxelemente auswählen** deaktivieren.  
  
 Die Spalten in diesem Dialogfeld enthalten die folgenden Informationen:  
  
 Name  
 Führt die Namen der Workflowaktivitäten auf, die aktuell auf dem lokalen Computer registriert sind.  
  
 Namespace  
 Zeigt die Hierarchie der Namespaces der .NET Framework\-Klassenbibliothek an, welche die Struktur der Aktivität definiert.  
  
 Assemblyname  
 Zeigt den Namen und die Version der .NET Framework\-Assembly an, die die Aktivität enthält.  
  
 Directory  
 Zeigt den Speicherort der .NET Framework\-Assembly an, die die Workflowaktivitäten enthält.Der Standardspeicherort für alle Assemblys ist der globale Assemblycache.  
  
 Klicken Sie zum Sortieren der aufgeführten Komponenten auf eine beliebige Spaltenüberschrift.