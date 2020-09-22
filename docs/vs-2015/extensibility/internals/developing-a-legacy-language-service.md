---
title: Entwickeln eines Legacy sprach Dienstanbieter | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 36ff8335bfaf99b5826d217a48910bfd581321e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841043"
---
# <a name="developing-a-legacy-language-service"></a>Entwickeln eines Legacysprachdiensts
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dieser Abschnitt ist mit Themen verknüpft, die Sie beim Erstellen eines Legacy sprach Dienstanbieter unterstützen.  
  
 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen zur neuen Methode zum Implementieren eines sprach Dienstanbieter finden Sie unter [Editor-und Sprachdienst Erweiterungen](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Modell eines Legacysprachdiensts](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Stellt ein Modell eines minimalen sprach Dienstanbieter für den [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Kern-Editor bereit. Sie können dieses Modell als Leitfaden zum Erstellen Ihres eigenen sprach Dienstanbieter verwenden.  
  
 [Schnittstellen von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Erläutert die Objekte, die zum Implementieren eines sprach Dienstanbieter erforderlich sind, und stellt eine Auflistung zusätzlicher Objekte bereit, mit denen Sie Syntax Hervorhebung, Methoden Daten und andere Funktionen bereitstellen können.  
  
 [Abfangen von Befehlen von Legacysprachdiensten](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Beschreibt, wie Sie einen Befehls Filter in ihren Sprachdienst einfügen, um Befehle abzufangen, die von der Textansicht andernfalls behandelt werden.  
  
 [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Enthält Informationen zum Registrieren Ihres sprach Dienstanbieter mithilfe von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Sprachdienstunterstützung für das Debuggen](../../extensibility/internals/language-service-support-for-debugging.md)  
 Beschreibt, wie ein Sprachdienst Funktionen bereitstellen kann, um einen Debugger zu unterstützen.  
  
 [Prüfliste: Erstellen eines Legacysprachdiensts](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Enthält Schritt-für-Schritt-Anleitungen zum Erstellen und integrieren eines sprach Dienstanbieter für den Kern-Editor.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Syntaxfarben in einem Legacysprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Erläutert, wie Syntax Hervorhebung in ihren Sprachdienst implementiert wird.  
  
 [Anweisungsvervollständigung in einem Legacysprachdienst](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Erläutert die Anweisungs Vervollständigung, den Prozess, mit dem ein Sprachdienst Benutzern hilft, ein sprach Schlüsselwort oder Element, das Sie eingegeben haben, zu beenden.  
  
 [Parameterinformationen in einem Legacysprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Beschreibt, wie Methoden Tipps für überladene Funktionen und Methoden bereitgestellt werden.  
  
 [Gewusst wie: Unterstützen von ausgeblendetem Text in einem Legacysprachdienst](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Erläutert den Zweck eines ausgeblendeten Text Bereichs und stellt Anweisungen zum Implementieren eines ausgeblendeten Text Bereichs bereit.  
  
 [Gewusst wie: Bereitstellen von Unterstützung für erweiterte Gliederungen in einem Legacysprachdienst](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Erläutert die beiden Optionen, die die Gliederung der Unterstützung für Ihre Sprache über die Unterstützung des Befehls Reduzierungs *Definitionen* hinaus erweitern.
