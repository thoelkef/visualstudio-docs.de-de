---
title: Parameterinformationen in einem Legacy-Sprachdienst1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c26073252aae5434ba5a8197955948d0d9ec883d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706801"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Parameterinformationen in einem Legacysprachdienst
Die IntelliSense Parameter Info-Tooltip gibt Benutzern Hinweise, wo sie sich in einem Sprachkonstrukt befinden.

 Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen finden Sie unter [Erweitern des Editors und der Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Es wird empfohlen, die neue Editor-API so schnell wie möglich zu verwenden. Dadurch wird die Leistung Ihres Sprachdienstes verbessert und Sie können die neuen Editorfunktionen nutzen.

## <a name="how-parameter-info-tooltips-work"></a>Funktionsweise von Parameterinfo-Tooltips
 Wenn Sie eine Anweisung in den Editor eingeben, zeigt das VSPackage ein kleines QuickInfo-Fenster an, das die Definition der eingegebenen Anweisung enthält. Wenn Sie beispielsweise eine MFC-Anweisung (Microsoft Foundation `pMainFrame ->UpdateWindow`Classes) eingeben (z. B. ) und die öffnende Klammertaste `UpdateWindow` drücken, um mit der Auflistung von Parametern zu beginnen, wird eine Methodenspitze angezeigt, die die Definition der Methode anzeigt.

 Parameter Info Tooltips werden in der Regel in Verbindung mit der Anweisungsvervollständigung verwendet. Sie sind besonders nützlich für Sprachen, die Parameter oder andere formatierte Informationen nach dem Methodennamen oder Schlüsselwort haben.

 Die Parameterinfo-Tooltips werden vom Sprachdienst durch Befehlsabfangen initiiert. Um Benutzerzeichen abzufangen, muss das <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Sprachdienstobjekt die Schnittstelle implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> und die Textansicht einen Zeiger an die Implementierung übergeben, indem es die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Methode in der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle aufruft. Der Befehlsfilter fängt Befehle ab, die Sie in das Codefenster eingeben. Überwachen Sie die Befehlsinformationen, um zu wissen, wann dem Benutzer Parameterinformationen angezeigt werden sollen. Sie können denselben Befehlsfilter für die Anweisungsvervollständigung, Fehlermarkierungen usw. verwenden.

 Wenn Sie ein Schlüsselwort eingeben, für das der Sprachdienst <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> Hinweise bereitstellen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> kann, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> erstellt der Sprachdienst ein Objekt und ruft die Methode in der Schnittstelle auf, um die IDE zu benachrichtigen, um einen Hinweis anzuzeigen. Erstellen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> Sie `VSLocalCreateInstance` das Objekt mit `CLSID_VsMethodTipWindow`der coclass und geben Sie sie an. `VsLocalCreateInstance`ist eine in der Headerdatei vsdoc.h definierte Funktion, die die lokale Registrierung aufruft `QueryService` und dieses Objekt für die `CreateInstance` `CLSID_VsMethodTipWindow`aufruft.

## <a name="providing-a-method-tip"></a>Bereitstellen eines Methodentipps
 Um einen Methodentipp bereitzustellen, rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> Methode in der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> Schnittstelle auf und übergeben Sie die Implementierung der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> Schnittstelle.

 Wenn <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> Ihre Klasse aufgerufen wird, werden ihre Methoden in der folgenden Reihenfolge aufgerufen:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Gibt die Position und Länge der relevanten Daten im aktuellen Textpuffer zurück. Dadurch wird die IDE angewiesen, diese Daten nicht mit dem QuickInfo-Fenster zu verschleiern.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Gibt die Methodennummer (Null-basierter Index) zurück, die ursprünglich angezeigt werden soll. Wenn Sie z. B. Null zurückgeben, wird zunächst die erste überladene Methode angezeigt.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Gibt die Anzahl der überladenen Methoden zurück, die im aktuellen Kontext anwendbar sind. Wenn Sie einen Wert größer als 1 für diese Methode zurückgeben, werden in der Textansicht pfeillange Nach- und Abwärtspfeile angezeigt. Wenn Sie auf den Abwärtspfeil <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> klicken, ruft die IDE die Methode auf. Wenn Sie auf den Pfeil nach <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> oben klicken, ruft die IDE die Methode auf.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Der Text der Parameterinfo-Tooltip wird während <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> mehrerer Aufrufe von the and-Methoden erstellt.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Gibt die Anzahl der Parameter zurück, die in der Methode angezeigt werden sollen.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Wenn Sie eine Methodennummer zurückgeben, die der Angezeigten überladen ist, wird <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> diese Methode aufgerufen, gefolgt von einem Aufruf der Methode.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Informiert Ihren Sprachdienst, um den Editor zu aktualisieren, wenn ein Methodentipp angezeigt wird. Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> Sie in der Methode Folgendes auf:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Sie erhalten einen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> Aufruf der Methode, wenn Sie das Methodentippfenster schließen.
