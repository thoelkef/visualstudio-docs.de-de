---
title: "Quelldateien debuggen, Allgemeine Eigenschaften, Eigenschaftenseiten (Dialogfeld) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.options.FindSource"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugquelldateien (Eigenschaftenseite)"
  - "Debuggen [Visual Studio], Angeben von Quell-und Symboldateien"
  - "Quelldateien, Angeben im Debugger"
  - "Debugger, Quelldateien"
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Quelldateien debuggen, Allgemeine Eigenschaften, Eigenschaftenseiten (Dialogfeld)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Auf dieser Eigenschaftenseite wird angegeben, wo der Debugger beim Debuggen der Projektmappe nach Quelldateien sucht.  
  
 Zum Öffnen der Eigenschaftenseite **Quelldateien debuggen** klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die betreffende Projektmappe und wählen dann im Kontextmenü **Eigenschaften** aus.  Erweitern Sie den Ordner **Allgemeine Eigenschaften**, und klicken Sie auf die Seite **Quelldateien debuggen**.  
  
 **Verzeichnisse mit Quellcode**  
 Darin enthalten ist eine Liste der Verzeichnisse, in denen der Debugger beim Debuggen der Projektmappe nach Quelldateien sucht.  Unterverzeichnisse der angegebenen Verzeichnissen werden ebenfalls durchsucht.  
  
 **Nach folgenden Quelldateien nicht suchen**  
 Geben Sie hier die Namen aller Quelldateien ein, die vom Debugger nicht gelesen werden sollen.  Wird eine dieser Dateien vom Debugger in einem der oben angegebenen Verzeichnisse gefunden, wird diese ignoriert.  Wenn während des Debuggens das Dialogfeld **Quellcode suchen** angezeigt wird und Sie auf **Abbrechen** klicken, wird die gesuchte Datei dieser Liste hinzugefügt, sodass der Debugger nicht länger nach dieser Datei sucht.  
  
## Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Einstellungen und Vorbereitung für das Debuggen](../debugger/debugger-settings-and-preparation.md)