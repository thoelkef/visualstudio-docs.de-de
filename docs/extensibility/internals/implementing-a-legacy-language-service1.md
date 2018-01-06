---
title: "Implementieren eine Vorgängerversion Language \"Service1\" | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 304d99c1ddd5fdfddba0c4df88fc4eeeb9dcb7ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-a-legacy-language-service"></a>Implementieren einen Sprachdienst Legacy
Verwenden Sie Klassen im des managed Package Framework (MPF) um ein legacy-Sprachdienst zu implementieren, der eine Vielzahl von Funktionen unterstützt, z. B. syntaxhervorhebung, Erkennung von zugehörigen Klammern und IntelliSense-Vervollständigung.  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Weitere Informationen über die neue Möglichkeit, einen Sprachdienst zu implementieren, finden Sie unter [-Editor und Dienst Spracherweiterungen](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht über Legacysprachdienste](../../extensibility/internals/legacy-language-service-overview.md)  
 Eine Übersicht über die Dienst-Sprachfunktionen, die in MPF unterstützt werden.  
  
 [Implementieren einen Sprachdienst Legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Beschreibt, was so implementieren Sie einen Sprachdienst mithilfe von MPF erforderlich ist.  
  
 [Registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Beschreibt die Schritte, die erforderlich sind, registrieren Sie einen Dienst MPF-basierte Sprache, mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Parser und Scanner von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Beschreibt die zwei Parser, die erforderlich sind, um alle Funktionen eines Sprachdiensts mithilfe des MPFS zu implementieren.  
  
 [Exemplarische Vorgehensweise: Erstellen eines Legacysprachdiensts](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Enthält die grundlegenden Schritte, die erforderlich sind, ein MPF-Sprachdienst in einem VSPackage implementiert.  
  
 [Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte (Legacyimplementierung)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Veranschaulicht die Techniken zum Abrufen einer Liste der installierten Codeausschnitte.  
  
 [Legacy-Dienst-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)  
 Enthält Links zu Themen, welche Aktionen ausgeführt werden müssen, auf um alle Funktionen eines Sprachdiensts zu implementieren, indem Sie mithilfe von MPF, Detail.