---
title: Legacy Language Service Grundlagen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 501bccf755293e86e8a9dc23fce125a10c882376
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707421"
---
# <a name="legacy-language-service-essentials"></a>Grundlagen zu Legacysprachdiensten
Sie müssen einen Sprachdienst bereitstellen, um eine Programmiersprache in Visual Studio zu integrieren. In diesem Thema werden die Funktionen erläutert, die in älteren Sprachdiensten verfügbar sind.

 Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen zur neuen Möglichkeit zum Implementieren eines Sprachdienstes finden Sie unter [Editor- und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Es wird empfohlen, die neue Editor-API so schnell wie möglich zu verwenden. Dadurch wird die Leistung Ihres Sprachdienstes verbessert und Sie können die neuen Editorfunktionen nutzen.

 Ältere Sprachdienste bieten die folgenden Funktionen:

|Funktion|BESCHREIBUNG|
|-------------|-----------------|
|Farben für Syntax|Bewirkt, dass die Editoransicht unterschiedliche Farben und Schriftarten für die verschiedenen Elemente einer Sprache anzeigt. Diese Differenzierung kann das Lesen und Bearbeiten von Dateien erleichtern.<br /><br /> Allgemeine Informationen finden Sie unter [Syntaxfarben in einem Legacy-Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Informationen zu dieser Funktion im Managed Package Framework (MPF) finden Sie unter [Syntax colorizing in a Legacy Language Service](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|
|Anweisungsvervollständigung|Schließt eine Anweisung oder ein Schlüsselwort ab, die der Benutzer mit der Eingabe begonnen hat. Die Anweisungsvervollständigung hilft Benutzern, schwierige Anweisungen leichter einzugeben, mit weniger Eingabe und weniger Fehlerchancen.<br /><br /> Allgemeine Informationen finden Sie [unter Statement-Abschluss in einem Legacy Language Service](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Informationen zu dieser Funktion in der MPF finden Sie unter [Word-Abschluss in einem Legacy-Sprachdienst](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|
|Klammernabgleich (zugehörige Klammer)|Hebt gepaarte Zeichen wie geschweifte Klammern hervor. Wenn der Benutzer ein schließendes Zeichen wie z. B. "A" eingibt, hebt der Abgleich der Geschweifdatei das entsprechende Eröffnungszeichen, wie z. B. "A", hervor. Wenn es mehrere Ebenen von einschließenden Zeichen gibt, hilft diese Funktion Benutzern zu bestätigen, dass die einschließenden Zeichen korrekt gekoppelt sind.<br /><br /> Weitere Informationen zu dieser Funktion in der MPF finden Sie unter [Brace Matching in a Legacy Language Service](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|
|Parameterinformationen QuickInfos|Zeigt eine Liste möglicher Signaturen für die überladene Methode an, die der Benutzer gerade eingibt.<br /><br /> Allgemeine Informationen finden Sie unter [Parameterinformationen in einem Legacy Language Service](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Informationen zu dieser Funktion in der MPF finden Sie unter [Parameterinformationen in einem Legacy Language Service](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|
|Fehlermarkierungen|Zeigt eine wellige rote Unterstreichung, auch als Squiggly bezeichnet, unter Text an, der syntaktisch falsch ist. Fehlermarkierungen werden in der Regel verwendet, um Benutzer auf falsch geschriebene Schlüsselwörter, nicht gesperrte Klammern, ungültige Zeichen und ähnliche Fehler aufmerksam zu machen.<br /><br /> In den MPF-Klassen werden Fehlermarkierungen <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> automatisch in <xref:Microsoft.VisualStudio.Package.AuthoringSink> der Methode der Klasse behandelt.|

 Viele dieser Funktionen erfordern den Sprachdienst, um Quellcode zu analysieren. Häufig können Sie den Tokenisierungs- und Analysecode für ihren Compiler oder Interpreter wiederverwenden.

 Die folgenden Funktionen beziehen sich auf die Unterstützung von Programmiersprachen, sind jedoch nicht Teil von Sprachdiensten:

| Funktion | BESCHREIBUNG |
|-----------------------| - |
| Ausdrucksauswertungen | Unterstützt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den Debugger, indem er Haltepunkte validiert und eine Liste von Ausdrücken eingibt, die im **Auto-Debugfenster** angezeigt werden sollen.<br /><br /> Weitere Informationen finden Sie unter [Sprachdienstunterstützung zum Debuggen](../../extensibility/internals/language-service-support-for-debugging.md). |
| Symbol-Browsing-Tools | Unterstützt **Object Browser**, Class **View**, Call **Browser**und Find **Symbol Results**. |
