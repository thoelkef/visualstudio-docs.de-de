---
title: "Der Projekttyp wird von dieser Installation nicht unterst&#252;tzt. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.projectflavornotavailable"
ms.assetid: 50e92aff-3ce9-4600-94af-4a16e9dffc90
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Der Projekttyp wird von dieser Installation nicht unterst&#252;tzt.
Dieser Fehler tritt auf, wenn Sie versuchen, einen Projekttyp zu öffnen, für den ein Software Development Kit \(SDK\) erforderlich ist, das nicht mit Visual Studio installiert wird.  Dieser Fehler tritt beispielsweise auf, wenn Sie Visual Studio auf einem Computer öffnen, auf dem das Visual Studio SDK nicht installiert ist, und anschließend versuchen, eine Projektdatei für dieses SDK zu öffnen, wie etwa ein VSIX\-Projekt. \(Weitere Informationen über das Visual Studio SDK finden Sie unter [Erweitern von Visual Studio](http://go.microsoft.com/fwlink/?LinkID=64968).\)  
  
## Problemumgehung  
 Sie müssen sicherstellen, dass das korrekte SDK für den Projekttyp, den Sie gerade zu öffnen versuchen, installiert ist.  
  
#### So überprüfen Sie, ob das SDK bereits installiert ist  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
2.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Installiert** und den Knoten **Vorlagen**, und wählen Sie dann den Knoten **Andere Projekttypen** aus.  
  
3.  Überprüfen Sie die verfügbaren Projekttypen, um zu bestimmen, ob das Projekt, das Sie zu öffnen versuchen, verfügbar ist.  
  
 Wenn Sie den Projekttyp, den Sie zu öffnen versuchen, nicht finden, ist das zugeordnete SDK nicht installiert.  Sie müssen das zugeordnete SDK finden und installieren, um den Projekttyp öffnen zu können.  
  
## Siehe auch  
 [Neues in Visual Studio 2015](../ide/what-s-new-in-visual-studio-2015.md)   
 [Portieren, Migrieren und Aktualisieren von Visual Studio\-Projekten](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)