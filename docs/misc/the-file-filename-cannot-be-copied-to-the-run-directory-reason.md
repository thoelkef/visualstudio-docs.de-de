---
title: "Die Datei &quot;Dateiname&quot; kann nicht in das Ausf&#252;hrungsverzeichnis kopiert werden. &lt;Ursache&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cant_copy_to_run_dir"
ms.assetid: 80474e62-7cef-48e9-a7c0-820345d5b591
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Die Datei &quot;Dateiname&quot; kann nicht in das Ausf&#252;hrungsverzeichnis kopiert werden. &lt;Ursache&gt;
Dieser Fehler wird angezeigt, wenn:  
  
-   ein Verweis, dessen `CopyLocal`\-Eigenschaft \(siehe das Fenster „Eigenschaften“, wenn der Verweis im Projektmappen\-Explorer ausgewählt ist\) auf `true` festgelegt ist, nicht in das Verzeichnis kopiert werden konnte, aus dem das Projekt ausgeführt wird.  
  
-   eine Abhängigkeit eines Verweises, dessen `CopyLocal`\-Eigenschaft auf `true` festgelegt ist, nicht in das Verzeichnis kopiert werden konnte, aus dem das Projekt ausgeführt wird.  
  
-   eine andere Datei, die lokal kopiert werden musste, nicht in das Verzeichnis kopiert werden kann, aus dem das Projekt ausgeführt wird.  
  
 In den meisten Fällen gibt die am Ende der Fehlermeldung aufgeführte `reason` an, dass die Datei von einem anderen Prozess verwendet wird. Es ist wahrscheinlich, dass die Datei von einem anderen Element in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gesperrt ist.  
  
 Es kann ein Problem vorliegen, das damit zu tun, dass Projekte im selben Ausgabeverzeichnis erstellt werden. Ist dies der Fall, erstellen Sie die beiden Projekte in unterschiedlichen Verzeichnissen. Erfolgt das Erstellen in unterschiedlichen Verzeichnisse, kopiert das Projektsystem alle abhängigen Assemblys in das Ausgabeverzeichnis eines Projekts.  
  
 Wenn Sie die Ausgabe irgendeines Projekts hinzufügen, das Sie als Werkzeugkastenelement bearbeiten, werden die verwalteten Designer dazu veranlasst, den Verweis zu sperren.  
  
 Das Projektsystem kann das Ausgabeverzeichnis nicht aktualisieren, wenn die Ausgabe derzeit ausgeführt wird.  
  
 **So beheben Sie diesen Fehler**  
  
-   Überprüfen Sie den verfügbaren Speicherplatz des Computers.  
  
-   Überprüfen Sie, ob eine Überschreitung der durch das Dateisystem festgelegten MAX\_PATH\-Begrenzung vorliegt.  
  
     Ein Vorliegen dieser Situation verhindert nicht, dass das Projekt erstellt wird. Allerdings kann dies bewirken, dass das Projekt nicht ordnungsgemäß ausgeführt wird, weil diese Warnung angibt, dass eine private Kopie einer Assembly, auf die verwiesen wird, nicht ordnungsgemäß aktualisiert werden konnte. Obwohl das Projekt scheinbar ordnungsgemäß ausgeführt wird, treten beim Ausführen bestimmter Codepfade möglicherweise TypeLoadException\-Ausnahmen oder ein unerwartetes Verhalten auf.  
  
## Siehe auch  
 [NIB: Gewusst wie: Festlegen der Eigenschaft „Lokale Kopie“ eines Verweises](http://msdn.microsoft.com/de-de/dfe2ba13-f27f-4356-a481-ea67d5acacbd)