---
title: 'Vorgehensweise: Ändern Sie den Namespace einer domänenspezifischen Sprache | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 19b756fb6957a22959614f63b93123f5cde817b5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209026"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Gewusst wie: Ändern des Namespace einer domänenspezifischen Sprache
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
 [DSL-Tools – Glossar](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



