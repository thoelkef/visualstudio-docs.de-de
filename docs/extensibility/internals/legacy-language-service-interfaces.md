---
title: Dienstschnittstellen Legacysprache | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c5c907885e91cc3b7765ff94528a30a84b17ee46
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909564"
---
# <a name="legacy-language-service-interfaces"></a>Schnittstellen von Legacysprachdiensten
Für die einer bestimmten Programmiersprache kann nur eine Instanz von einem Sprachdienst zu einem Zeitpunkt vorhanden sein. Allerdings kann ein einzelnes Sprachdienst mehr als ein Editor dienen.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] einen Sprachdienst mit einem bestimmten-Editor wird keine Beziehung zwischen. Wenn Sie die Sprache des Dienstvorgangs anfordern, müssen Sie die geeigneten Editor als Parameter identifizieren.

## <a name="common-interfaces-associated-with-language-services"></a>Allgemeine Schnittstellen Sprachdienste
 Der Editor Ruft den Sprachdienst durch Aufrufen von <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> für das VSPackage, geeignet. Der Dienst-ID (SID) in diesem Aufruf übergebenen identifiziert den Sprachdienst, der angefordert wird.

 Sie können Language Service Kernschnittstellen auf eine beliebige Anzahl von separate Klassen implementieren. Allerdings ist eine gängige Methode in einer einzelnen Klasse die folgenden Schnittstellen:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (optional)

  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle muss auf die Dienste für alle Sprachen implementiert werden. Er bietet Informationen zu den Sprachdienst, z. B. den lokalisierten Namen der Sprache, die Dateinamenerweiterungen, die der Sprachdienst und zum Abrufen einer Farbauswahl zugeordnet.

## <a name="additional-language-service-interfaces"></a>Zusätzlichen Sprachdienst-Schnittstellen
 Andere Schnittstellen können mit den Sprachdienst bereitgestellt werden. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fordert eine separate Instanz dieser Schnittstellen für jede Instanz des Textpuffers. Aus diesem Grund sollten Sie jede dieser Schnittstellen auf sein eigenes Objekt implementieren. Die folgende Tabelle zeigt die Schnittstellen, die eine Instanz pro Instanz des Text-Puffer erfordern.

|Interface|Beschreibung|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Verwaltet die Zusatzelemente des Code-Fenster, z. B. die Dropdownleiste an. Sie können diese Schnittstelle abrufen, indem Sie mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> Methode. Es gibt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> pro Code-Fenster.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Farbliche Darstellung Programmiersprachen-Schlüsselwörter und Trennzeichen. Sie können diese Schnittstelle abrufen, indem Sie mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Methode. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> wird zum Zeitpunkt der Paint aufgerufen werden. Vermeiden Sie rechenintensive Aufgaben in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> oder konnte die Leistung beeinträchtigt werden.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Stellt Parameter IntelliSense-QuickInfo bereit. Wenn der Sprachdienst erkennt ein Zeichen, der angibt, Methodendaten muss angezeigt werden, z. B. eine öffnende Klammer ruft er die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> -Methode benachrichtigt den Text anzuzeigen, die der Sprachdienst ist für die Anzeige einer Parameter-QuickInfo bereit. Die Textansicht klicken Sie dann einen Rückruf in den Sprachdienst, indem Sie mithilfe der Methoden der der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> -Schnittstelle zum Abrufen der erforderlichen Informationen für die Anzeige der QuickInfo.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Stellt IntelliSense-Anweisungsvervollständigung bereit. Wenn der Sprachdienst bereit, um eine Vervollständigungsliste anzuzeigen ist, ruft er die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode in der Textansicht. Die Textansicht klicken Sie dann einen Rückruf in den Sprachdienst, indem Sie mit den Methoden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> Objekt.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Ermöglicht die Änderung von der Textansicht, die den Befehlshandler verwenden. Die Klasse, in dem Sie implementieren, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Schnittstelle muss auch implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Ruft die Textansicht ab, der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Objekt durch Abfragen der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Objekt, das übergebene ist die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Methode. Ein SqlEndAltersStep vorhanden sein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Objekt für jede Ansicht.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Fängt Befehle, dass der Benutzer in das Codefenster Typen ab. Überwachen Sie die Ausgabe Ihrer <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Implementierung zum Bereitstellen von Informationen über den Abschluss der benutzerdefinierten und Anzeigen von Änderungen<br /><br /> Übergeben Ihrer <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Objekt, das die Textansicht, Aufruf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|

## <a name="see-also"></a>Siehe auch
- [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Prüfliste: Erstellen eines Legacysprachdiensts](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)