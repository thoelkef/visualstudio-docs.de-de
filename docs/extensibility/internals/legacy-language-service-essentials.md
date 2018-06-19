---
title: Ältere Language Service Essentials | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 68b92b821ad77b050ad2116da6fd930b975dad5a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135444"
---
# <a name="legacy-language-service-essentials"></a>Ältere Language Service Essentials
Sie müssen einen Sprachdienst zum Integrieren von eines Programmiersprache Ihrer Wahl in Visual Studio bereitstellen. Dieser Artikel beschreibt die Funktionen, die in älteren Sprachdienste verfügbar.  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Weitere Informationen über die neue Möglichkeit, einen Sprachdienst zu implementieren, finden Sie unter [-Editor und Dienst Spracherweiterungen](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
 Dienste für ältere Sprachen bieten folgende Funktionen:  
  
|Feature|Beschreibung|  
|-------------|-----------------|  
|Farben für Syntax|Bewirkt, dass die Editor-Ansicht, um andere Farben und Schriftarten für die verschiedenen Elemente von einer anderen Sprache anzuzeigen. Diese Unterscheidung erleichtern das Lesen und Bearbeiten von Dateien.<br /><br /> Allgemeine Informationen finden Sie unter [Färbung Syntax in ein Legacy-Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Informationen zu dieser Funktion in des managed Package Framework (MPF) finden Sie unter [farbliche Kennzeichnung von Syntax in ein Legacy-Sprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Anweisungsvervollständigung|Schließt eine Anweisung oder ein Schlüsselwort, das der Benutzer eingeben gestartet wurde. Anweisungsvervollständigung hilft Benutzern, die schwer Anweisungen leichter, mit weniger Aufwand und weniger potenzielle Fehler eingeben.<br /><br /> Allgemeine Informationen finden Sie unter [Anweisungsvervollständigung in einen Legacy-Sprachdienst](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Informationen zu dieser Funktion in des verwalteten Paketframeworks finden Sie unter [Wortvervollständigung in einen Legacy-Sprachdienst](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Zugehörige Klammer|Highlights gekoppelt Zeichen wie z. B. geschweifte Klammern. Wenn der Benutzer eingibt eine schließenden Klammer wie z. B. "}", Klammer hervorgehoben, die entsprechenden öffnenden Zeichen, z. B. "{". Wenn mehrere Ebenen von einschließenden Zeichen vorhanden sind, kann diese Funktion Benutzer bestätigen, dass die umschließenden Zeichen ordnungsgemäß miteinander kombiniert sind.<br /><br /> Informationen zu dieser Funktion in des verwalteten Paketframeworks finden Sie unter [Klammer in einen Legacy-Sprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Parameter Informationen QuickInfos|Zeigt eine Liste der möglichen Signaturen für die überladene Methode, die der Benutzer derzeit eine Eingabe ist.<br /><br /> Allgemeine Informationen finden Sie unter [ParameterInfo in einen Legacy-Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Informationen zu dieser Funktion in des verwalteten Paketframeworks finden Sie unter [ParameterInfo in einen Legacy-Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Fehler-Marker|Zeigt eine rote Wellenlinie, auch bekannt als eine Wellenlinie, unter dem Text, die syntaktisch falsch ist. Fehler-Marker werden normalerweise verwendet, um Benutzer falsch geschriebene Schlüsselwörter, nicht geschlossene Klammern, ungültige Zeichen und ähnliche Fehler erkennen.<br /><br /> In den MPF-Klassen werden Fehler Marker automatisch behandelt die <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> Methode der <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse.|  
  
 Viele dieser Funktionen erfordern der Sprachdienst, Quellcode zu analysieren. Sie können häufig die Tokenisierung und Analysieren von Code für Ihre Compiler oder einem Interpreter wiederverwenden.  
  
 Die folgenden Funktionen stehen im Zusammenhang mit der übrigen Programmiersprachen unterstützt, jedoch sind nicht Teil der Dienste für Sprachen:  
  
|Feature|Beschreibung|  
|-------------|-----------------|  
|Ausdrucksauswertungen|Unterstützt die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger durch Überprüfen von Haltepunkten und Angabe einer Liste von Ausdrücken, die in angezeigt werden die **"Auto"** Debug-Fenster.<br /><br /> Weitere Informationen finden Sie unter [Dienst sprachunterstützung zum Debugging](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Tools zum Durchsuchen des Symbols|Unterstützt **Objektkatalog**, **Klassenansicht**, **Browser aufrufen**, und **Ergebnisse der Symbolsuche**.|