---
title: ParameterInfo in eines Legacysprachdiensts 1 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6727dc1da1a91dab52c7a194dd82c51f83368e5f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196468"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Parameterinformationen in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die IntelliSense-ParameterInfo-QuickInfo bietet Benutzern Hinweise, wo sie sich in einem Sprachkonstrukt sind.  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Wenn Sie mehr erfahren möchten, finden Sie unter [Erweitern des Editors und Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="how-parameter-info-tooltips-work"></a>Funktionsweise von QuickInfo-Tipps für Parameter  
 Wenn Sie eine Anweisung im Editor eingeben, zeigt das VSPackage ein kleines QuickInfo-Fenster, das mit der Definition der-Anweisung eingegeben wird. Angenommen, Sie geben Sie eine Microsoft Foundation Classes (MFC)-Anweisung (z. B. `pMainFrame ->UpdateWindow`), und drücken Sie die öffnende Klammer ein Schlüssel, um zu beginnen, Auflisten von einem methodentipp angezeigt wird, mit der Definition der Parameter, die `UpdateWindow` Methode.  
  
 Parameter-QuickInfo-Tipps werden normalerweise in Verbindung mit der Anweisungsvervollständigung verwendet werden. Sie sind besonders hilfreich für die Sprachen, die Parameter oder andere formatierte Informationen nach dem Methodennamen oder das Schlüsselwort verfügen.  
  
 Die ParameterInfo-QuickInfo werden vom Sprachdienst durch Abfangen von Befehlen initiiert. Zum Abfangen von Benutzer-Zeichen, das Language-Dienstobjekt implementieren muss die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle ab und übergeben Sie die Ansicht für den einen Zeiger auf Ihre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Implementierung durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> -Methode in der die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle. Der Befehlsfilter fängt Befehle, die Sie in das Codefenster eingeben. Überwachen Sie die Befehlsinformationen, um zu wissen, wann Informationen zu den Parametern, die dem Benutzer angezeigt. Sie können den gleichen Befehlsfilter für die Anweisungsvervollständigung, fehlermarker und So weiter verwenden.  
  
 Wenn Sie ein Schlüsselwort eingeben, für die der Sprachdienst Hinweise bereitstellen kann, klicken Sie dann der Sprachdienst erstellt eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> -Objekt und ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> -Methode in der die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle zum Benachrichtigen der IDE einen Hinweis angezeigt. Erstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> -Objekt unter Verwendung der `VSLocalCreateInstance` und geben Sie die Co-Klasse `CLSID_VsMethodTipWindow`. `VsLocalCreateInstance` ist eine Funktion, die in der vsdoc.h der Header-Datei, die aufruft, definiert `QueryService` für die lokale Registrierung und ruft `CreateInstance` für dieses Objekt für die `CLSID_VsMethodTipWindow`.  
  
## <a name="providing-a-method-tip"></a>Bereitstellen einer Methodentipp  
 Um eine methodentipp bereitzustellen, rufen die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> -Methode in der die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> -Schnittstelle, und übergeben sie die Implementierung von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> Schnittstelle.  
  
 Wenn Ihre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> -Klasse aufgerufen wird, deren Methoden aufgerufen werden, in der folgenden Reihenfolge:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Gibt die Position und Länge der relevanten Daten in den aktuellen Textpuffer zurück. Dies weist die IDE nicht auf diese Daten mit dem QuickInfo-Fenster verdeckt.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Gibt die Methode-Anzahl (nullbasiert) zuerst angezeigt werden soll. Z. B. Wenn Sie 0 (null) zurückgegeben wird, wird dann die erste überladene Methode zunächst präsentiert.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Gibt die Anzahl der überladenen Methoden, die im aktuellen Kontext anwendbar sind. Wenn Sie einen Wert größer als 1 für diese Methode zurückgegeben wird, zeigt die Textansicht nach oben oder unten Pfeile für Sie. Wenn Sie den Pfeil nach unten klicken, ruft die IDE die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> Methode. Wenn Sie den Pfeil nach oben klicken, ruft die IDE die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> Methode.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     Das ParameterInfo-QuickInfo erstellt wird, während mehrere Aufrufe der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> Methoden.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Gibt die Anzahl von Parametern, die in der Methode angezeigt.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Wenn Sie, eine Methodennummer, die mit der Überladung zurückkehren, angezeigt werden sollen, diese Methode wird aufgerufen, gefolgt von einem Aufruf der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> Methode.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Informiert den Sprachdienst, um den Editor zu aktualisieren, wenn es sich bei einem methodentipp angezeigt wird. In der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> -Methode den folgenden Aufruf:  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Sie erhalten einen Anruf an die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> Methode, wenn Sie das Fenster des methodentipps schließen.

