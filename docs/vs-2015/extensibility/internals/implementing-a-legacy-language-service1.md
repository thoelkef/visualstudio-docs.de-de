---
title: Implementieren eines Legacysprachdiensts 1 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5c2a258eb573f0f7d685cdb5a1159df29761944
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765021"
---
# <a name="implementing-a-legacy-language-service"></a>Implementieren eines Legacysprachdiensts
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sie können einen legacysprache-Dienst implementiert, der eine Vielzahl von Funktionen unterstützt Klassen in das managed Package Framework (MPF) verwenden, wie syntaxhervorhebung, zugehörige Klammern und IntelliSense-Vervollständigung.  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Um mehr über die neue Methode zum Implementieren von eines Sprachdiensts zu suchen, finden Sie unter [-Editor und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht über Legacysprachdienste](../../extensibility/internals/legacy-language-service-overview.md)  
 Eine Übersicht über die Dienst-Sprachfunktionen, die in MPF unterstützt werden.  
  
 [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Beschreibt, was zu einen Sprachdienst zu implementieren, indem Sie mithilfe von MPF erforderlich ist.  
  
 [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Beschreibt die Schritte, die erforderlich sind, registrieren Sie eine MPF-basierten Sprachdienst mit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Parser und Scanner von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Beschreibt die zwei Parser, die erforderlich sind, um alle Features von einem Sprachdienst zu implementieren, mithilfe des MPFS.  
  
 [Exemplarische Vorgehensweise: Erstellen eines Legacysprachdiensts](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Enthält die grundlegenden Schritte, die erforderlich sind, eine MPF-Sprachdienst in einem VSPackage implementiert.  
  
 [Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte (Legacyimplementierung)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Zeigt die Techniken zum Abrufen einer Liste der installierten Codeausschnitte an.  
  
 [Funktionen von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)  
 Enthält Links zu Themen mit Details, um alle Features von einem Sprachdienst zu implementieren, indem Sie mithilfe von MPF durchgeführt werden müssen.

