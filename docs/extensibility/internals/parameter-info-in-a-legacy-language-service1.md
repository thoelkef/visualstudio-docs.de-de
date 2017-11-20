---
title: ParameterInfo in ein Legacy-Language "Service1" | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f3fd29f46f0edb184b3e0cd5e6ddc766ffc94de
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="parameter-info-in-a-legacy-language-service"></a>ParameterInfo in einen Legacy-Sprachdienst
Die ParameterInfo IntelliSense-QuickInfo Benutzern Hinweise, in denen ein Sprachkonstrukt werden bereitgestellt.  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Wenn Sie mehr erfahren möchten, finden Sie unter [Erweiterung des Editors und des Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="how-parameter-info-tooltips-work"></a>Funktionsweise von QuickInfos Parameter  
 Wenn Sie eine Anweisung im Editor eingeben, zeigt das VSPackage eine kleine QuickInfo-Fenster, die mit der Definition der Anweisung eingegeben wird. Z. B., wenn Sie eine Anweisung für die Microsoft Foundation Classes (MFC) eingeben (z. B. `pMainFrame ->UpdateWindow`), und drücken Sie die öffnende Klammer Taste gestartet werden sollen Parameter ein Methode Tipp angezeigt wird, Anzeigen der Definition der `UpdateWindow` Methode.  
  
 Parameter QuickInfos werden normalerweise in Verbindung mit der Anweisungsvervollständigung verwendet. Sie sind besonders hilfreich für die Sprachen, die Parameter oder andere formatierte Informationen nach dem Methodennamen oder Schlüsselwort.  
  
 Die ParameterInfo QuickInfos werden von der Sprachdienst, über den Befehl abfangen gestartet. Zum Abfangen von Benutzer-Zeichen, das Language-Dienstobjekt implementieren muss die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle, und übergeben Sie die Ansicht für den einen Zeiger auf die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Implementierung durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Methode in der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle. Der Befehlsfilter fängt Befehle, die Sie in das Codefenster eingeben. Überwachen Sie die Befehlsinformationen, um zu erfahren, wann die Parameterinformationen für den Benutzer anzuzeigen. Sie können den gleichen Befehlsfilter für die Anweisungsvervollständigung, den Fehler Marker usw. verwenden.  
  
 Bei der Eingabe ein Schlüsselwort für die der Sprachdienst Hinweise bereitstellen kann, klicken Sie dann der Sprachdienst erstellt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> -Objekt und ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> Methode in der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle zum Benachrichtigen der IDE einen Hinweis angezeigt. Erstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> -Objekt mit `VSLocalCreateInstance` und Angeben der Coklasse `CLSID_VsMethodTipWindow`. `VsLocalCreateInstance`ist eine Funktion, die in der vsdoc.h der Header-Datei, die aufruft `QueryService` für die lokale Registrierung und ruft `CreateInstance` für dieses Objekt für die `CLSID_VsMethodTipWindow`.  
  
## <a name="providing-a-method-tip"></a>Bereitstellen eines Methode Tipps  
 Um einen Tipp Methode bereitzustellen, rufen die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> Methode in der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> -Schnittstelle, und übergeben sie die Implementierung von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> Schnittstelle.  
  
 Wenn Ihre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> -Klasse aufgerufen wird, deren Methoden aufgerufen werden, in der folgenden Reihenfolge:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Gibt die Position und Länge der relevanten Daten in der aktuellen Textpuffer zurück. Dadurch wird die IDE nicht Daten über das QuickInfo-Fenster verdeckt angewiesen.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Gibt die Methode zurück (nullbasiert) anfänglich angezeigt werden soll. Z. B. Wenn Sie 0 (null) zurückgeben, wird anschließend die erste überladene Methode anfänglich angezeigt.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Gibt die Anzahl der überladenen Methoden, die im aktuellen Kontext verfügbar sind. Wenn Sie einen Wert größer als 1 ist für diese Methode zurückgeben, zeigt die Textansicht Pfeiltasten für Sie. Wenn Sie den Pfeil nach unten klicken, ruft die IDE die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> Methode. Wenn Sie den Pfeil nach oben klicken, ruft die IDE die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> Methode.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     Der Text der QuickInfo ParameterInfo erstellt wird, während mehrere Aufrufe an die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> Methoden.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Gibt die Anzahl von Parametern in der Methode angezeigt.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Wenn Sie, eine Methode Zahl entspricht, mit der Überladung, die angezeigt werden sollen zurückkehren, diese Methode wird aufgerufen, gefolgt von einem Aufruf der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> Methode.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Informiert die Sprachdienst, um den Editor zu aktualisieren, wenn eine Methode QuickInfo angezeigt wird. In der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> -Methode, rufen Sie die folgenden:  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Sie erhalten einen Anruf an den <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> Methode, wenn die Methode QuickInfo-Fenster zu schließen.