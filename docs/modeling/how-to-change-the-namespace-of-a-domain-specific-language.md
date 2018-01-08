---
title: "Vorgehensweise: Ändern Sie den Namespace einer domänenspezifischen Sprache | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: "19"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 3d0dbf6c74c309972862db460f2536d8c6b16801
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Gewusst wie: Ändern des Namespace einer domänenspezifischen Sprache
Sie können den Namespace einer domänenspezifischen Sprache ändern. Sie müssen die Änderungen in der **Explorer für DSL**, in den Eigenschaften des Projekts Dsl-Paket und die Assemblyinformationen.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>So ändern Sie den Namespace einer domänenspezifischen Sprache  
  
1.  In **Explorer für DSL**, klicken Sie auf die **Dsl** Knoten.  
  
2.  In der **Eigenschaften** Ändern der **Namespace** Eigenschaft.  
  
3.  Speichern Sie die Projektmappe, und Transformieren Sie die Vorlagen zu.  
  
4.  Auf der **Projekt** Menü klicken Sie auf **Dsl Eigenschaften**.  
  
     Die Eigenschaften für das Projekt werden angezeigt.  
  
5.  Klicken Sie auf die Registerkarte **Anwendung** .  
  
6.  Ändern der **Standardnamespace** Eigenschaft in den neuen Namespacenamen.  
  
7.  Wenn Sie auch den Namen der Assembly ändern möchten, ändern Sie die **Assemblyname (Eigenschaft).**  
  
8.  Wenn Sie den Assemblynamen geändert haben, öffnen Sie DslPackage\Package.tt, und aktualisieren Sie diese Zeile:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Wenn Sie benutzerdefinierten Code verfasst haben, stellen Sie sicher, die Namespace- und Klassennamen Verweise in den Codedateien zu ändern.  
  
10. Setzen Sie die Visual Studio experimentelle Instanz zurück.  
  
    1.  Löschen Sie **\Users\\***{Ihr Name}***\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2.  Auf der Windows **starten** Menü Wählen Sie **Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**, **Zurücksetzen der Experimentelle Instanz**.  
  
11. Auf der **erstellen** Menü wählen **Projektmappe neu erstellen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)