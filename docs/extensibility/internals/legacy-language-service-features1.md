---
title: Ältere Language Service Features1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 12acd0690c11e61baedf358dec193e4f6da601e8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-language-service-features"></a>Legacy-Dienst-Sprachfunktionen
Mindestens ein verwalteten Package Framework (MPF)-Sprachdienst unterstützen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Funktionen, z. B. syntaxhervorhebung, IntelliSense und Validierung der Haltepunkt. Jede Funktion kann unabhängig von den anderen implementiert werden, aber alle erfordern einen Parser und einen Scanner mit Ausnahme von syntaxhervorhebung, der nur einen Scanner erforderlich ist.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Zugehörige Klammer in einem Legacysprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Beschreibt, was zur Unterstützung von Sprache paarvergleich, auch bekannt als Zuordnung von geschweiften Klammern erforderlich ist.  
  
 [Kommentieren von Code in einem Legacysprachdienst](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Beschreibt, was zur Unterstützung von Kommentieren und die auskommentierung des ausgewählten Codes erforderlich ist.  
  
 [Benutzerdefinierte Dokumenteigenschaften in einem Legacysprachdienst](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Beschreibt, was ist zur Unterstützung von Dokumenteigenschaften, die in einer Quelldatei eingebettet sind.  
  
 [Gliederung in einem Legacysprachdienst](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Beschreibt, was Unterstützung durch die Implementierung des ausgeblendete Bereiche Gliederung erforderlich ist.  
  
 [Neuformatieren von Code in einem Legacysprachdienst](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Beschreibt, was zur Unterstützung von umformatieren Code erforderlich ist.  
  
 [Unterstützen von Codeausschnitten in einem Legacysprachdienst](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Beschreibt, was ist erforderlich, um Codeausschnitte, unterstützen die Segmente des Codes sind, die eingefügt werden und kann bearbeitet werden.  
  
 [ParameterInfo in einen Legacy-Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Beschreibt, was ist zur Unterstützung des ParameterInfo IntelliSense-Vorgangs für die Signatur einer Methode anzeigen, wie die Methode eingegeben wurde.  
  
 [QuickInfo in einem Legacysprachdienst](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Beschreibt, was zur Unterstützung des Vorgangs IntelliSense-QuickInfo für die Anzeige von Informationen über einen Bezeichner erforderlich ist.  
  
 [Membervervollständigung in einem Legacysprachdienst](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Beschreibt, was erforderlich ist, zur Unterstützung des IntelliSense-Member-Abschluss-Vorgangs für ein Mitglied eines Namespaces aus einer Liste auswählen.  
  
 [Wortvervollständigung in einem Legacysprachdienst](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Beschreibt, was zur Unterstützung des IntelliSense-Wort vervollständigen-Vorgangs für teilweise typisierte Vervollständigung erforderlich ist.  
  
 [Unterstützen des Auto-Fensters in einem Legacysprachdienst](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Beschreibt ein Sprachdienst Möglichkeiten zur Unterstützung der **"Auto"** Fenster, die während des Debuggens.  
  
 [Unterstützen der Navigationsleiste in einem Legacysprachdienst](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Beschreibt, wie die **Navigationsleiste** am oberen Rand der Editor-Ansicht zum Bereitstellen von schnelle Navigation für Typen oder Member in der Datei, die in dieser Ansicht angezeigt...  
  
 [Einfärben der Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Beschreibt, was zur Unterstützung der syntaxhervorhebung des Quellcodes erforderlich ist.  
  
 [Überprüfen von Haltepunkten in einem Legacysprachdienst](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Beschreibt, was ein Sprachdienst tun kann, um die Überprüfung Haltepunkte außerhalb eines Debuggers zu unterstützen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Parser und Scanner von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Beschreibt die Parser und Scanner, die erforderlich sind, um alle Funktionen eines Sprachdiensts implementiert wird, des managed Package Framework verwendet.  
  
 [Implementieren einen Sprachdienst Legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Beschreibt, was zum Implementieren eines Sprachdiensts mithilfe des MPFS erforderlich ist.  
  
 [Registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Beschreibt die Schritte, die erforderlich sind, registrieren Sie einen Dienst MPF-basierte Sprache, mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Verwenden von IntelliSense](../../ide/using-intellisense.md)  
 Erläutert, wie IntelliSense Sprachreferenzen problemlos zugegriffen wird.  
  
 [Implementieren einen Sprachdienst Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Enthält Informationen dazu, wie mithilfe des managed Package Framework (MPF) einen voll ausgestattete Sprachdienst in verwaltetem Code implementiert.