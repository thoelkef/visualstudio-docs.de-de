---
title: "Gewusst wie: &#196;ndern des Namespace einer dom&#228;nenspezifischen Sprache | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Namespace"
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 19
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 19
---
# Gewusst wie: &#196;ndern des Namespace einer dom&#228;nenspezifischen Sprache
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können den Namespace einer domänenspezifischen Sprache ändern.  Sie müssen die Änderung **DSL\-Explorer**, an den Eigenschaften des Dsl\-Paket projekts und den Assemblyinformationen vornehmen.  
  
### So ändern Sie den Namespace einer domänenspezifischen Sprache  
  
1.  In **DSL\-Explorer**klicken Sie auf den Knoten **Dsl** .  
  
2.  Im **Eigenschaften** Fenster ändern Sie die **Namespace**\-Eigenschaft.  
  
3.  Speichern Sie die Projektmappe, und Sie die Vorlagen transformieren.  
  
4.  Zeigen Sie im Menü **ProjektDSL\-Eigenschaften**.  
  
     Die Eigenschaften für das Projekt werden.  
  
5.  Klicken Sie auf die Registerkarte **Anwendung**.  
  
6.  Ändern Sie die **Standardnamespace**\-Eigenschaft auf den neuen Namespacenamen.  
  
7.  Wenn Sie auch den Namen der Assembly ändern möchten, ändern Sie **Eigenschaft "Assemblyname".**  
  
8.  Wenn Sie den Assemblynamen geändert haben, aktualisieren DslPackage \\ öffnen und Package.tt folgende Zeile:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Wenn Sie einen benutzerdefinierten Code geschrieben haben, dass Sie die Namespace\- und Klassen Verweise in den Codedateien zu ändern.  
  
10. Setzen Sie die experimentelle Instanz von Visual Studio zurück.  
  
    1.  Löschen Sie **\\Users\\***{Name}***\\AppData\\Local\\Microsoft\\VisualStudio\\\*Exp**  
  
    2.  Klicken Sie im Windows\-Startmenü wählen Sie **Alle Programme**, **Microsoft Visual Studio 2010 SDK**, **Extras**, **Experimentelle Instanz zurücksetzen**aus.  
  
11. Zeigen Sie im Menü **ErstellenProjektmappe neu erstellen**aus.  
  
## Siehe auch  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/de-de/ca5e84cb-a315-465c-be24-76aa3df276aa)