---
title: "Resource transformation for file &#39;file&#39; failed. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.resx_generator_failed"
ms.assetid: 6b537d38-1da9-4f5f-9ae9-1f26e260c2ac
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Resource transformation for file &#39;file&#39; failed. &lt;reason&gt;
Die Verarbeitung durch den Ressourcenprozessor, der zur Umwandlung von RESX\-Dateien in binäre Ressourcendateien verwendet wird, ist fehlgeschlagen.  Die genaue Ursache \(falls vorhanden\) wird an das Ende der Zeichenfolge angehängt.  Der Buildprozess schlägt fehl, wenn dieser Fehler auftritt.  
  
 Dieser Fehler wird meistens durch eine fehlerhafte RESX\-Datei verursacht.  Möglicherweise ist die Datei in einem Texteditor geöffnet und geändert worden.  
  
 Wenn die Fehlermeldung "Das Element wurde bereits hinzugefügt.  Schlüssel im Wörterbuch: 'NewControlName.\<Eigenschaftenname\>' Hinzuzufügender Schlüssel: 'ControlName.\<Eigenschaftenname\>" mit einer \<Ursache\> angegeben wird, beachten Sie die folgenden Schritte, um den Fehler zu reproduzieren und zu korrigieren.  
  
### So reproduzieren Sie diesen Fehler  
  
1.  Erstellen Sie eine neue Windows\-Anwendung.  Standardmäßig wird Form1 erstellt.  
  
2.  Klicken Sie im Menü **Ansicht** auf **Eigenschaften**.  
  
3.  Legen Sie im **Eigenschaftenfenster** die **Localizable**\-Eigenschaft auf `True` fest.  
  
4.  Klicken Sie in den **Eigenschaftenfenstern** auf **Sprache**, und legen Sie dann den Wert auf "Japanisch" fest.  
  
5.  Ziehen Sie eine Schaltfläche von der Toolbox auf das Formular.  
  
6.  Ändern Sie den Namen der Schaltfläche von "Button1" in "BUTTON1".  
  
7.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
### So beheben Sie diesen Fehler  
  
1.  Zeigen Sie im Menü **Datei** auf **Öffnen**, und klicken Sie auf **Datei**.  
  
2.  Suchen Sie die Datei Form1.resx, und klicken Sie dann auf **OK**.  Form1.resx wird angezeigt.  
  
3.  Suchen Sie die ursprünglichen Schlüsselwerte, und löschen Sie sie dann manuell aus der Datenliste.  Angenommen, Sie verfügen über eine Schaltfläche mit dem Namen "Button1".  Sie ändern den Namen dieser Schaltfläche in "BUTTON1."  Die Schlüsselwerte sowohl für "Button1" als auch für "BUTTON1" befinden sich in Form1.resx.  Entfernen Sie alle Einträge von "Button1", und erstellen Sie dann das Projekt neu.  
  
## Siehe auch  
 [Resources in .Resx File Format](http://msdn.microsoft.com/de-de/0c476133-87e4-47e8-b0ef-4b88f4ef3dc5)   
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/de-de/f793852c-da06-4d52-a826-65f635844772)