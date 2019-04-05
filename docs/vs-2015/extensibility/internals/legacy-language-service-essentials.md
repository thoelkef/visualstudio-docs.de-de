---
title: Grundlagen zu Legacysprachdiensten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88e2b07fe640c2b9c69259cfc9ec48d98594bd6f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961131"
---
# <a name="legacy-language-service-essentials"></a>Grundlagen zu Legacysprachdiensten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sie müssen einen Sprachdienst, zum Integrieren von einer Programmiersprache in Visual Studio bereitstellen. Dieser Artikel beschreibt die Funktionen von legacy-Sprachdienste an.  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Um mehr über die neue Methode zum Implementieren von eines Sprachdiensts zu suchen, finden Sie unter [-Editor und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
 Legacy-Sprachdienste bieten die folgenden Features:  
  
|Feature|Beschreibung|  
|-------------|-----------------|  
|Farben für Syntax|Bewirkt, dass die Editor-Ansicht, um verschiedene Farben und Schriftarten für die verschiedenen Elemente von einer anderen Sprache anzuzeigen. Diese Unterscheidung kann einfacher zu lesen und Bearbeiten von Dateien.<br /><br /> Weitere Informationen finden Sie unter [Färbung Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Weitere Informationen zu dieser Funktion in das managed Package Framework (MPF), finden Sie unter [einfärben der Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Anweisungsvervollständigung|Schließt eine Anweisung oder ein Schlüsselwort, das der Benutzer begonnen hat eingeben. Anweisungsvervollständigung hilft Benutzern, die schwierige Anweisungen leichter, mit weniger Code eingeben und weniger wahrscheinlich Fehler geben.<br /><br /> Weitere Informationen finden Sie unter [Anweisungsvervollständigung in einem Legacysprachdienst](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Weitere Informationen zu diesem Feature die MPF finden Sie unter [Wortvervollständigung in einem Legacysprachdienst](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Überprüfung des Klammergleichgewichts|Highlights gekoppelt Zeichen wie z. B. von geschweiften Klammern. Wenn der Benutzer eingibt eine schließenden Klammer wie z. B. "}", Klammern hervorgehoben werden den entsprechenden Zeichen, z. B. Öffnen "{". Wenn mehrere Ebenen von einschließenden Zeichen vorhanden sind, hilft dieses Feature Benutzer bestätigen, dass die umschließenden Zeichen ordnungsgemäß miteinander kombiniert sind.<br /><br /> Weitere Informationen zu diesem Feature die MPF finden Sie unter [Klammer in einem Legacysprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|QuickInfos für Parameter-Informationen|Zeigt eine Liste der möglichen Signaturen für die überladene Methode, die derzeit des Benutzers Eingabe.<br /><br /> Weitere Informationen finden Sie unter [Parameterinformationen in einem Legacysprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Weitere Informationen zu diesem Feature die MPF finden Sie unter [Parameterinformationen in einem Legacysprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Fehlermarker|Zeigt eine rote Wellenlinie, auch bekannt als eine Wellenlinie, unter dem Text, der syntaktisch falsch ist. Fehlermarker werden normalerweise verwendet, um Benutzer falsch geschriebene Schlüsselwörter, nicht geschlossene Klammern, ungültige Zeichen und ähnliche Fehler aufmerksam zu machen.<br /><br /> In die MPF-Klassen, fehlermarker automatisch behandelt werden die <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> Methode der <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse.|  
  
 Viele dieser Funktionen erfordern den Sprachdienst Quellcode analysieren. Sie können häufig die Tokenisierung und Analysieren von Code für Ihre Compiler oder einem Interpreter wiederverwenden.  
  
 Die folgenden Features stehen im Zusammenhang mit Unterstützung für Programmiersprachen, jedoch sind nicht Teil des Sprachdienste:  
  
|Feature|Beschreibung|  
|-------------|-----------------|  
|Ausdrucksauswertungen|Unterstützt die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugger durch Überprüfen von Haltepunkten und durch Angabe einer Liste von Ausdrücken in angezeigt werden die **"Auto"** Debug-Fenster.<br /><br /> Weitere Informationen finden Sie unter [Sprachdienstunterstützung für Debuggen](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Tools zum Durchsuchen von Symbolen|Unterstützt **Objektkatalog**, **Klassenansicht**, **Aufrufbrowser**, und **Ergebnisse der Symbolsuche**.|
