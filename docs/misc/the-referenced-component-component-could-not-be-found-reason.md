---
title: "The referenced component &#39;component&#39; could not be found. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.referencenotfound"
ms.assetid: 35491b4d-e3e4-4e7c-8ac1-3adb09c1ef58
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The referenced component &#39;component&#39; could not be found. &lt;reason&gt;
Das Projektsystem konnte einen bestimmten Verweis nicht auflösen.  Wenn Sie auf dieses Aufgabenlistenelement doppelklicken, wird der Fokus auf den Projektmappen\-Explorer festgelegt und der Verweis ausgewählt, der nicht aufgelöst werden konnte.  
  
 Bearbeiten Sie die [ReferencePath](http://msdn.microsoft.com/de-de/8e549b39-7256-456a-8fd7-089b23facf9c)\-Eigenschaft so, dass die entsprechenden Verzeichnisse im Pfad enthalten sind.  
  
 Dieser Fehler kann auftreten, wenn Sie ein Projekt auf einen anderen Computer verschieben.  Die `ReferencePath`\-Eigenschaft wird als absoluter Pfad gespeichert.  Wenn sich der Verweis R1 auf Computer A im Pfad c:\\R\\R1.dll befindet, wird in der Datei .vbproj.user oder .csproj.user c:\\R als Teil der `ReferencePath`\-Eigenschaft gespeichert.  Wenn sich jedoch auf Computer **B** der Verweis **R1** in **d:\\R\\R1.dll** befindet, kann das Projektsystem **R1** nicht finden, weil **d:\\R** sich nicht im Verweispfad befindet.  
  
 Ähnlich verhält es sich beim Szenario für das Quellcodesteuerelement.  Wenn Sie sich bei einem Projekt anmelden, wird die Datei **vvbproj.user** \(bzw. **csproj.user**\) nicht auf den Computer kopiert, da sie nicht im Quellcodesteuerelement gespeichert ist.  Aus diesem Grund ist der anfängliche Wert der `ReferencePath`\-Eigenschaft leer, und alle Verweise, deren Auflösung von `ReferencePath` abhängig ist, werden nicht aufgelöst.  Weitere Informationen finden Sie unter "Verwalten von Abhängigkeiten" in *Teamentwicklung mit Visual Studio .NET und Visual SourceSafe*.  
  
 Dieser Fehler kann auch entstehen, wenn ein Projekt, auf das verwiesen wird, sich nicht in der aktuellen Projektmappe befindet.  
  
 Wenn dieser Fehler auftritt, kann das Projekt eventuell nicht erstellt werden.  
  
 Weitere Informationen zum Auflösen von Assemblyverweisen finden Sie unter [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md).  
  
## Siehe auch  
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)