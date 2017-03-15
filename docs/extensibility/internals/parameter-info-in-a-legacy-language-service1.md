---
title: "ParameterInfo in einer Vorg&#228;ngerversion Language &quot;Service1&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Language Services, Methode Tipps"
  - "Methode Tipps"
  - "Language Services, Parameter-QuickInfo"
  - "IVsMethodData-Schnittstelle"
  - "ParameterInfo (IntelliSense)"
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# ParameterInfo in einer Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Parameter Info von IntelliSense\-QuickInfo bietet Benutzern Hinweise dazu, wo sie in einem Sprachkonstrukt sind.  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Um weitere Informationen finden Sie unter [Erweitern der\-Editor und Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor\-API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie die neue Editorfunktionen nutzen.  
  
## Funktionsweise von QuickInfos Parameter  
 Wenn Sie eine Anweisung im Editor eingeben, zeigt das VSPackage ein kleines QuickInfo\-Fenster mit der Definition der Anweisung, die eingegeben wird. Wenn Sie eine Microsoft Foundation Classes \(MFC\)\-Anweisung eingeben, z. B. \(z. B. `pMainFrame ->UpdateWindow`\), und drücken Sie die öffnende Klammer beginnen auflisten Parameter ein Methode Tipp angezeigt wird, mit der Definition der Schlüssel die `UpdateWindow` Methode.  
  
 Parameter QuickInfos werden normalerweise in Verbindung mit dem Abschluss der Anweisung verwendet. Sie sind besonders für Sprachen, die Parameter oder andere formatierte Informationen nach dem Methodennamen oder \-Schlüsselwort verfügen.  
  
 Die QuickInfos Parameter werden von der Sprachdienst über befehlsunterbrechung gestartet. Um Benutzer Zeichen abzufangen, muss das Language\-Dienstobjekt implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle, und übergeben Sie die Ansicht für den einen Zeiger auf Ihre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Implementierung durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> \-Methode in der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle. Der Befehlsfilter fängt Befehle, die Sie in das Codefenster eingeben. Überwachen Sie die Befehlsinformationen, um zu wissen, wann die Parameterinformationen für den Benutzer anzuzeigen. Sie können den gleichen Befehlsfilter für Anweisungsabschluss Fehler Marker und So weiter verwenden.  
  
 Bei der Eingabe ein Schlüsselwort für die der Sprachdienst Hinweise bereitstellen kann, der Sprachdienst erstellt dann ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> \-Objekt und ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> \-Methode in der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle zu benachrichtigen, die IDE einen Hinweis angezeigt. Erstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> \-Objekt unter Verwendung der `VSLocalCreateInstance` und Angeben der Co\-Klasse `CLSID_VsMethodTipWindow`.`VsLocalCreateInstance` ist eine Funktion, die in der Header\-Datei vsdoc.h, die Aufrufe definiert `QueryService` für die lokale Registrierung und ruft `CreateInstance` für dieses Objekt für die `CLSID_VsMethodTipWindow`.  
  
## Bereitstellen eines Methode Tipps  
 Um einen Tipp Methode bereitzustellen, rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> \-Methode in der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> \-Schnittstelle, und übergeben sie die Implementierung von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> Schnittstelle.  
  
 Wenn Ihre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> Klasse aufgerufen wird, deren Methoden aufgerufen werden, in der folgenden Reihenfolge:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Gibt die Position und Länge der relevanten Daten in der aktuellen Textpuffer zurück. Dieser Code weist die IDE nicht Daten über das QuickInfo\-Fenster verdeckt.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Gibt die Methode zurück \(nullbasiert\) Anfangs angezeigt werden soll. Beispielsweise wird NULL zurückgegeben, wird anschließend die erste überladene Methode anfänglich angezeigt.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Gibt die Anzahl der überladenen Methoden, die im aktuellen Kontext angewendet werden. Wenn Sie einen Wert größer als 1 für diese Methode zurückgegeben wird, zeigt die Textansicht Pfeiltasten für Sie. Wenn Sie auf den Pfeil nach unten klicken, ruft die IDE die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> Methode. Wenn Sie auf den Pfeil nach oben klicken, ruft die IDE die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> Methode.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     Der Text der QuickInfo ParameterInfo wird erstellt, während mehrere Aufrufe der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> Methoden.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Gibt die Anzahl der Parameter in der Methode angezeigt.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Wenn Sie, eine Methodennummer mit der Überladung, die angezeigt werden soll zurückkehren, diese Methode wird aufgerufen, gefolgt von einem Aufruf von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> Methode.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Informiert die Sprachdienst Editor zu aktualisieren, wenn ein Methode Tipp angezeigt wird. In der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> \-Methode den folgenden Aufruf:  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Sie erhalten einen Anruf an die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> \-Methode, wenn Sie die Methode QuickInfo\-Fenster schließen.