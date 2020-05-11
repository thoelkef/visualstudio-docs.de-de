---
title: Legacy Language Service-Schnittstellen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89d80d6961f5eaf91721567ccb0efa73bbe31406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707387"
---
# <a name="legacy-language-service-interfaces"></a>Schnittstellen von Legacysprachdiensten
Für jede bestimmte Programmiersprache kann es jeweils nur eine Instanz eines Sprachdienstes geben. Ein einzelner Sprachdienst kann jedoch mehr als einen Editor bedienen.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]einen Sprachdienst keinem bestimmten Editor zuzuordnen. Wenn Sie daher einen Sprachdienstvorgang anfordern, müssen Sie den entsprechenden Editor als Parameter identifizieren.

## <a name="common-interfaces-associated-with-language-services"></a>Gemeinsame Schnittstellen, die mit Sprachdiensten verknüpft sind
 Der Editor erhält Ihren <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> Sprachdienst, indem er das entsprechende VSPackage aufruft. Die in diesem Aufruf übergebene Dienst-ID (SID) identifiziert den angeforderten Sprachdienst.

 Sie können die zentralen Sprachdienstschnittstellen für eine beliebige Anzahl separater Klassen implementieren. Ein gängiger Ansatz besteht jedoch darin, die folgenden Schnittstellen in einer einzelnen Klasse zu implementieren:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (optional)

  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle muss für alle Sprachdienste implementiert werden. Sie enthält Informationen zu Ihrem Sprachdienst, z. B. den lokalisierten Namen der Sprache, die dem Sprachdienst zugeordneten Dateinamenerweiterungen und das Abrufen eines Colorizers.

## <a name="additional-language-service-interfaces"></a>Zusätzliche Sprachdienstschnittstellen
 Andere Schnittstellen können mit Ihrem Sprachdienst bereitgestellt werden. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fordert eine separate Instanz dieser Schnittstellen für jede Instanz des Textpuffers an. Daher sollten Sie jede dieser Schnittstellen für ein eigenes Objekt implementieren. Die folgende Tabelle zeigt Schnittstellen, die eine Instanz pro Textpufferinstanz erfordern.

|Schnittstelle|BESCHREIBUNG|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Verwaltet Codefensterverzierungen, z. B. die Dropdownleiste. Sie können diese Schnittstelle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> mithilfe der Methode abrufen. Es gibt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> ein S-pro-Code-Fenster.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Kolorisiert Sprachschlüsselwörter und Trennzeichen. Sie können diese Schnittstelle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> mithilfe der Methode abrufen. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>wird zur Malzeit aufgerufen. Vermeiden Sie rechenintensive <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Arbeit im Inneren oder die Leistung könnte leiden.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Stellt IntelliSense-Parameter-Tooltips bereit. Wenn der Sprachdienst ein Zeichen erkennt, das angibt, dass Methodendaten angezeigt werden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> sollen, z. B. eine geöffnete Klammer, ruft er die Methode auf, um die Textansicht zu benachrichtigen, dass der Sprachdienst bereit ist, eine Parameterinfo-ToolTip anzuzeigen. Die Textansicht ruft dann mithilfe der Methoden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> Schnittstelle in den Sprachdienst zurück, um die erforderlichen Informationen zum Anzeigen der QuickInfo abzubekommen.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Stellt die Vervollständigung der IntelliSense-Anweisung bereit. Wenn der Sprachdienst bereit ist, eine Abschlussliste anzuzeigen, ruft er die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode in der Textansicht auf. Die Textansicht ruft dann mithilfe von Methoden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> für das Objekt in den Sprachdienst zurück.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Ermöglicht die Änderung der Textansicht mithilfe des Befehlshandlers. Die Klasse, in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> der Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle implementieren, muss auch die Schnittstelle implementieren. Die Textansicht ruft <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> das Objekt <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ab, indem das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Objekt abgefragt wird, das an die Methode übergeben wird. Für jede <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Ansicht sollte ein Objekt vorhanden sein.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Fängt Befehle ab, die der Benutzer in das Codefenster eingibt. Überwachen der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Ausgabe aus Ihrer Implementierung, um benutzerdefinierte Abschlussinformationen bereitzustellen und Änderungen anzuzeigen<br /><br /> Um das <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Objekt an die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>Textansicht zu übergeben, rufen Sie an.|

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Prüfliste: Erstellen eines Legacysprachdiensts](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
