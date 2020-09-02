---
title: Anzeigen von Datenwerten in Daten Tipps im Code-Editor | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fd2c7bf67b5c2e7f25b4193462883b53cda8db87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700108"
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>Anzeigen von Datenwerten als Datentipps im Code-Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataTips stellen eine praktische Möglichkeit dar, um beim Debuggen Informationen über Variablen im Programm anzuzeigen. Sie können DataTips nur im Unterbrechungsmodus verwenden und nur mit Variablen, die sich im aktuellen Gültigkeitsbereich der Ausführung befinden.  
  
 In [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] können DataTips an eine bestimmte Position in einer Quelldatei angeheftet werden, oder Sie können über alle Fenster hinaus schweben [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>So zeigen Sie DataTips an (nur im Unterbrechungsmodus)  
  
1. Platzieren Sie in einem Quellcodefenster den Mauszeiger auf eine beliebige Variable aus dem aktuellen Gültigkeitsbereich.  
  
    Ein DataTip wird angezeigt.  
  
   > [!NOTE]
   > DataTips werden immer in dem Kontext ausgeführt, in dem die Ausführung angehalten wird, und nicht an der Stelle, auf die der Cursor zeigt. Wenn Sie in einer anderen Funktion auf eine Variable mit dem Namen einer Variablen im aktuellen Kontext zeigen, wird der Wert der Variablen in der anderen Funktion als der Wert der Variablen im aktuellen Kontext angezeigt.  
  
2. Der DataTip verschwindet, wenn Sie den Mauszeiger fortbewegen. Um den DataTip so anzuheften, dass er geöffnet bleibt, klicken Sie auf das Symbol **an Quelle** anheften.  
  
   - Klicken Sie mit der rechten Maustaste auf eine Variable, und klicken Sie auf **an Quelle**anheften  
  
     Der angeheftete DataTip wird geschlossen, wenn die Debugsitzung endet.  
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>So lösen Sie einen DataTip und zeigen diesen unverankert an  
  
- Klicken Sie in einem angehefteten DataTip auf das Symbol **aus Quelle lösen** .  
  
     Das Pinsymbol ändert sich in die gelöste Position. Der DataTip wird nun unverankert über allen geöffneten Fenstern angezeigt. Der unverankerte DataTip wird geschlossen, wenn die Debugsitzung endet.  
  
### <a name="to-repin-a-floating-datatip"></a>So heften Sie einen unverankerten DataTip wieder an  
  
- Klicken Sie in einem DataTip auf das Pinsymbol.  
  
     Das Pinsymbol ändert sich in die angeheftete Position. Wenn sich der DataTip außerhalb eines Quellcodefensters befindet, wird das Pinsymbol deaktiviert, und der DataTip kann nicht angeheftet werden.  
  
### <a name="to-close-a-datatip"></a>So schließen Sie einen DataTip  
  
- Platzieren Sie den Mauszeiger über einem DataTip, und klicken Sie dann auf das Symbol **Schließen** .  
  
### <a name="to-close-all-datatips"></a>So schließen Sie alle DataTips  
  
- Klicken Sie im Menü **Debuggen** auf **alle DataTips löschen**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>So schließen Sie alle DataTips für eine bestimmte Datei  
  
- Klicken Sie im Menü **Debuggen** auf alle an *Datei*angehefteten **DataTips löschen** .  
  
## <a name="expanding-and-editing-information"></a>Erweitern und Bearbeiten von Informationen  
 Mithilfe von DataTips können Sie ein Array, eine Struktur oder ein Objekt erweitern, um deren Member anzuzeigen. Sie können mit einem DataTip auch den Wert einer Variablen bearbeiten.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>So erweitern Sie eine Variable, um ihre Elemente anzuzeigen  
  
- Bewegen Sie den Mauszeiger in einem DataTip über das **+** Vorzeichen, das vor dem Variablennamen steht.  
  
     Die Variable wird erweitert, und die Elemente werden in Strukturansicht angezeigt.  
  
     Bei erweiterter Variable können Sie mit den Pfeiltasten der Tastatur nach oben und unten navigieren. Sie können auch die Maus verwenden.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>So bearbeiten Sie den Wert einer Variablen mit einem DataTip  
  
1. Klicken Sie in einem DataTip auf den Wert. Für schreibgeschützte Werte ist diese Funktion deaktiviert.  
  
2. Geben Sie einen neuen Wert ein, und drücken Sie die EINGABETASTE.  
  
## <a name="making-a-datatip-transparent"></a>Transparentes Darstellen eines DataTips  
 Wenn Sie den Code hinter einem DataTip sehen möchten, können Sie dazu den DataTip vorübergehend transparent machen. Dies gilt nicht für DataTips, die angeheftet oder unverankert sind.  
  
#### <a name="to-make-a-datatip-transparent"></a>So machen Sie einen DataTip transparent  
  
- Drücken Sie in einem DataTip STRG.  
  
     Der DataTip bleibt so lange transparent, wie Sie STRG gedrückt halten.  
  
## <a name="visualizing-complex-data-types"></a>Visuelles Darstellen von komplexen Datentypen  
 Wenn ein Lupensymbol neben einem Variablennamen in einem DataTip angezeigt wird, sind für Variablen dieses Datentyps mindestens ein [benutzerdefiniertes Fenster zum Erstellen von benutzerdefinierten Visualisierungen](../debugger/create-custom-visualizers-of-data.md) verfügbar. Mit der Schnellansicht lassen sich Informationen noch übersichtlicher (in der Regel über eine grafische Darstellung) anzeigen.  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>So zeigen Sie den Inhalt einer Variablen mithilfe der Schnellansicht an  
  
- Klicken Sie auf das Symbol mit dem Vergrößerungsglas, um die Standardschnellansicht für den Datentyp auszuwählen.  
  
     - oder -  
  
     Klicken Sie auf den Popup-Pfeil neben der Schnellansicht, und wählen Sie aus der Liste eine dem Datentyp entsprechende Schnellansicht aus.  
  
     Die Informationen werden in einer Schnellansicht angezeigt.  
  
## <a name="adding-information-to-a-watch-window"></a>Hinzufügen von Informationen zu einem Überwachungsfenster  
 Wenn Sie die Überwachung einer Variablen fortsetzen möchten, können Sie die Variable dem Fenster über **Wachen** von einem DataTip hinzufügen.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>So fügen Sie dem Überwachungsfenster eine Variable hinzu  
  
- Klicken Sie mit der rechten Maustaste auf einen DataTip, und klicken Sie auf **Überwachung hinzufügen**.  
  
     Die Variable wird dem **Überwachungs** Fenster hinzugefügt. Wenn Sie eine Edition verwenden, die mehrere **Überwachungs** Fenster unterstützt, wird die Variable zu **Überwachung 1** hinzugefügt.  
  
## <a name="importing-and-exporting-datatips"></a>Importieren und Exportieren von DataTips  
 Sie können DataTips in eine XML-Datei exportieren, die Sie gemeinsam mit Kollegen verwenden oder in einem Text-Editor bearbeiten können.  
  
#### <a name="to-export-datatips"></a>So exportieren Sie DataTips  
  
1. Klicken Sie im Menü Debuggen auf **DataTips exportieren**.  
  
     Das Dialogfeld **DataTips exportieren** wird angezeigt.  
  
2. Verwenden Sie standardmäßige Datei Techniken, um zu dem Speicherort zu navigieren, in dem Sie die XML-Datei speichern möchten, geben Sie im Feld **Dateiname** einen Namen für die Datei ein, und klicken Sie dann auf **OK**.  
  
#### <a name="to-import-datatips"></a>So importieren Sie DataTips  
  
1. Klicken Sie im Menü Debuggen auf **DataTips importieren**.  
  
     Das Dialogfeld **DataTips importieren** wird angezeigt.  
  
2. Verwenden Sie das Dialogfeld, um die XML-Datei zu suchen, die Sie öffnen möchten, und klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Gewusst wie: Verwenden des Dialog Felds "schnell Überwachung"](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Erstellen von benutzerdefinierten Visualisierungen](../debugger/create-custom-visualizers-of-data.md)   
 [Gewusst wie: Ändern des numerischen Formats von Debuggerfenstern](https://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)
