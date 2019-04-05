---
title: 'Vorgehensweise: Der Namespace einer domänenspezifischen Sprache ändern | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2a48c0692dcdcc93d58b5909b03b151ed7e1aae2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955486"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Vorgehensweise: Ändern des Namespace einer domänenspezifischen Sprache
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können den Namespace einer domänenspezifischen Sprache ändern. Sie müssen die Änderung, die **DSL-Explorer**, in den Eigenschaften des Projekts Dsl-Paket und die Assembly-Informationen.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>So ändern Sie den Namespace einer domänenspezifischen Sprache  
  
1.  In **DSL-Explorer**, klicken Sie auf die **Dsl** Knoten.  
  
2.  In der **Eigenschaften** Ändern der **Namespace** Eigenschaft.  
  
3.  Speichern Sie die Projektmappe, und Transformieren Sie die Vorlagen zu.  
  
4.  Auf der **Projekt** Menü klicken Sie auf **Dsl Eigenschaften**.  
  
     Die Eigenschaften für das Projekt angezeigt werden.  
  
5.  Klicken Sie auf die Registerkarte **Anwendung** .  
  
6.  Ändern der **Standardnamespace** Eigenschaft, um den neuen Namespacenamen.  
  
7.  Wenn Sie auch den Namen der Assembly ändern möchten, ändern Sie die **Assemblyname (Eigenschaft).**  
  
8.  Wenn Sie den Assemblynamen geändert haben, öffnen Sie DslPackage\Package.tt, und aktualisieren Sie diese Zeile:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Wenn Sie keinen benutzerdefinierten Code geschrieben haben, stellen Sie sicher, dass die Namespace- und Klassennamen Verweise in den Codedateien zu ändern.  
  
10. Setzen Sie die experimentelle Instanz Visual Studio zurück.  
  
    1.  Löschen Sie **\Users\\**_{Ihr Name}_**\AppData\Local\Microsoft\VisualStudio\\\*"exp"**  
  
    2.  Auf der Windows **starten** Menü wählen **Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**, **Zurücksetzen der Experimentelle Instanz**.  
  
11. Auf der **erstellen** Menü wählen **Projektmappe neu erstellen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
