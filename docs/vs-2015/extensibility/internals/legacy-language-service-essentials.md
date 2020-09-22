---
title: Legacy Sprachdienst-Grundlagen | Microsoft-Dokumentation
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
ms.openlocfilehash: a3926ff84f3b2e6415df1ca7333409c05d839685
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840844"
---
# <a name="legacy-language-service-essentials"></a>Grundlagen zu Legacysprachdiensten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sie müssen einen Sprachdienst bereitstellen, um eine Programmiersprache in Visual Studio zu integrieren. In diesem Thema werden die in den Legacy Sprachdiensten verfügbaren Features erläutert.  
  
 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen zur neuen Methode zum Implementieren eines sprach Dienstanbieter finden Sie unter [Editor-und Sprachdienst Erweiterungen](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.  
  
 Legacy Sprachdienste bieten die folgenden Features:  
  
|Feature|BESCHREIBUNG|  
|-------------|-----------------|  
|Farben für Syntax|Bewirkt, dass in der Editor-Ansicht verschiedene Farben und Schriftarten für die verschiedenen Elemente einer Sprache angezeigt werden. Diese Differenzierung erleichtert das Lesen und Bearbeiten von Dateien.<br /><br /> Allgemeine Informationen finden Sie unter [Syntax Farbgebung in einem Legacy Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Informationen zu diesem Feature im Managed Package Framework (MPF) finden Sie unter [Syntax Farbgebung in einem Legacy Sprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Anweisungsvervollständigung|Schließt eine-Anweisung oder ein-Schlüsselwort ab, mit der der Benutzer begonnen hat. Mit der Anweisungs Vervollständigung können Benutzer schwierige Anweisungen leichter eingeben, mit weniger Typisierung und weniger Fehler Chancen.<br /><br /> Allgemeine Informationen finden Sie unter [Anweisungs Vervollständigung in einem Legacy Sprachdienst](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Informationen zu diesem Feature im MPF finden Sie unter [Wortvervollständigung in einem Legacy Sprachdienst](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Klammernabgleich (zugehörige Klammer)|Hebt die Hervorhebung von paarweise paarweise Verknüpfungs Zeichen Wenn der Benutzer ein Schließ Endes Zeichen, z. b. "}", eingibt, wird das entsprechende öffnende Zeichen, wie z. b. "{", durch die Klammer Wenn mehrere Ebenen von einschließenden Zeichen vorhanden sind, können Benutzer mit dieser Funktion bestätigen, dass die einschließenden Zeichen ordnungsgemäß gekoppelt werden.<br /><br /> Weitere Informationen zu diesem Feature im MPF finden Sie unter [Abgleichen von Klammern in einem Legacy Sprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Tooltipps für Parameter Informationen|Zeigt eine Liste möglicher Signaturen für die überladene Methode an, die der Benutzer gerade eingibt.<br /><br /> Allgemeine Informationen finden Sie unter [Parameter Informationen in einem Legacy Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Informationen zu diesem Feature im MPF finden Sie unter [Parameter Info in einem Legacy Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Fehler Marker|Zeigt eine wellenförmige rote Unterstreichung, auch als Wellenlinien bezeichnet, unter Text an, der syntaktisch nicht korrekt ist. Fehler Marker werden normalerweise verwendet, um Benutzern die Kenntnis von falsch geschriebenen Schlüsselwörtern, nicht schließenden Klammern, ungültigen Zeichen und ähnlichen Fehlern zu ermöglichen.<br /><br /> In den MPF-Klassen werden Fehler Marker automatisch in der- <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> Methode der- <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse behandelt.|  
  
 Viele dieser Features erfordern, dass der Sprachdienst Quellcode analysiert. Sie können den tokenisierungs-und-Code für den Compiler oder den Interpreter häufig wieder verwenden.  
  
 Die folgenden Funktionen beziehen sich auf die Unterstützung von Programmiersprachen, sind jedoch nicht Teil der Sprachdienste:  
  
|Feature|BESCHREIBUNG|  
|-------------|-----------------|  
|Ausdrucks Auswertung|Unterstützt den [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugger durch Überprüfen von Breakpoints und Bereitstellen einer Liste von Ausdrücken, die **Autos** im Fenster Auto Debug angezeigt werden sollen.<br /><br /> Weitere Informationen finden Sie [unter Sprachdienst Unterstützung für das Debuggen](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Tools zum Durchsuchen von Symbolen|Unterstützt **Objektkatalog**-, **Klassenansicht**-, **Aufrufbrowser**-und Such **Symbol Ergebnisse**.|
