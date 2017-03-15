---
title: "Ank&#252;ndigen der Auswahlnachverfolgung im Eigenschaftenfenster | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK], Unterstützung von Eigenschaftenseiten"
  - "Eigenschaftenseiten, Nachverfolgen der Auswahl"
  - "Eigenschaftenfenster, Nachverfolgen der Auswahl"
  - "Auswahl, Nachverfolgen"
  - "Editoren [Visual Studio SDK], Unterstützung des Eigenschaftenfensters"
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Ank&#252;ndigen der Auswahlnachverfolgung im Eigenschaftenfenster
Wenn Sie mit dem **Eigenschaften** Fenster arbeiten möchten oder die **Eigenschaft** Seiten, z. B. ein Formular, Text, oder für den eine Auswahl von Eigenschaften finden möchte, müssen Sie verfügen über vollständige Kenntnis davon, wie Sie die Auswahl koordinieren.  Beispielsweise müssen Sie wissen, ob Sie einzelne Auswahl oder Mehrfachauswahl verfügen.  Sie müssen dann den Auswahltyp \(Single oder mehreren Sie in der IDE\) mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>\-Schnittstelle ankündigen.  Diese Schnittstelle stellt die Informationen bereit, die vom **Eigenschaften** Fenster erforderlich sind.  
  
### So fügen Sie ankündigen Umgebung zur Auswahl  
  
1.  Aufruf `QueryInterface` für <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>.  
  
    1.  Hierzu verwenden Sie den Zeiger Website, die an die Ansicht übergeben wird, als er erstellt wurde.  
  
    2.  Rufen Sie `QueryService` aus der Ansicht für den `SID_STrackSelection` Dienst an.  
  
         Dies gibt einen Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>zurück.  
  
2.  Rufen Sie die Methode <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> jedes Mal, wenn sich die Auswahl ändert auf, und übergeben Sie einen Zeiger auf ein Objekt, das <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>implementiert.  
  
     Durch Auswahl containerobjekt kann entweder mit Mehrfachauswahl oder aussondern die Auswahl und enthalten Informationen in einem `IDispatch`\-Objekt.  Die <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> Aufrufen der Methode benachrichtigt das **Eigenschaften** Fenster, dass die Auswahl geändert hat.  Das **Eigenschaften** Fenster verwendet dann die Objekte auf <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , um zu bestimmen, ob einzeln oder Mehrfachauswahl aufgetreten sind und welche tatsächlichen Objekt\-Auswahl ist.  
  
     Wenn Sie eine Mehrfachauswahl angeben, sucht das **Eigenschaften** Fenster die Schnittmenge einer allgemeinen Eigenschaften für die Objekte.  Wenn Sie eine einzelne Objekt\-Auswahl angeben, wird das Fenster **Eigenschaften** alle Eigenschaften für das ein Objekt an.  
  
## Siehe auch  
 [Erweitern von Eigenschaften](../extensibility/internals/extending-properties.md)   
 [Eigenschaftenseiten](../extensibility/internals/property-pages.md)