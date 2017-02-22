---
title: "Gewusst wie: Bereitstellen von Kontext f&#252;r Editoren | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - bereitzustellen Kontext."
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Bereitstellen von Kontext f&#252;r Editoren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Kontext ist für einen Editor aktiv, nur, wenn der Editor den Fokus besitzt, oder fokussiert, unmittelbar bevor der Fokus auf ein Fenster verschoben wurde. Sie können den Kontext für einen Editor angeben, wie folgt:  
  
1.  Erstellen Sie einen kontextbehälter.  
  
2.  Veröffentlichen Sie die Kontextsammlung auf die Auswahl\-Element\-ID \(SEID\).  
  
3.  Behalten Sie den Kontext im Behälter.  
  
 Diese Aufgaben werden durch die folgenden Verfahren behandelt. Weitere Informationen über das Bereitstellen von Kontext finden Sie unter **Robuste Programmierung** weiter unten in diesem Thema.  
  
### So erstellen Sie einen kontextbehälter für einen Editor oder designer  
  
1.  Rufen Sie `QueryService` auf Ihre <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Schnittstelle für die <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> Service.  
  
     Ein Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> \-Schnittstelle wird zurückgegeben.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> Methode, um einen neuen Kontext oder Unterkontext Behälter zu erstellen.  
  
     Ein Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> \-Schnittstelle wird zurückgegeben.  
  
3.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> \-Methode Kontext oder Unterkontext Behälter Attribute, Lookup\-Schlüsselwörter oder F1\-Schlüsselwörter hinzu.  
  
4.  Wenn Sie einen Unterkontext Behälter erstellen, rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> Unterkontext Behälter für die übergeordnete Kontextsammlung verknüpft.  
  
5.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> Benachrichtigung bei der **Dynamische Hilfe** Fenster aktualisiert wird.  
  
     Mit der **Dynamische Hilfe** Fenster Editor aufrufen zur Aktualisierung wird er bietet Ihnen die Möglichkeit, den Kontext zu ändern, bis die Aktualisierung wird verzögert. Auf diese Weise kann die Leistung verbessern, weil dadurch zu verzögern, zeitaufwändige Algorithmen ausgeführt, bis die Leerlaufzeit des Systems verfügbar ist.  
  
### Der kontextbehälter in der SEID veröffentlichen  
  
1.  Rufen Sie `QueryService` auf die <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> Service zur Rückgabe eines Zeigers auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> Schnittstelle.  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, Festlegung einer Element\-ID \(`elementid` Parameter\) Wert des SEID\_UserContext, um anzugeben, dass Sie den Kontext auf globaler Ebene übergeben.  
  
3.  Wenn der Editor oder Designer aktiv ist, die Werte in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> Objekt werden an die globale Auswahl weitergegeben. Sie müssen nur zum Abschließen dieser einmal pro Sitzung, und speichern dann den Zeiger auf den globalen Kontext erstellt, wenn Sie aufgerufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.  
  
### Verwalten der kontextbehälter  
  
1.  Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> sicherstellen, dass die **Dynamische Hilfe** Fenster Editor oder Designer aufgerufen, bevor sie aktualisiert.  
  
     Für jede kontextbehälter, die aufgerufen wird, hat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> nachdem der kontextbehälter erstellt und implementiert, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, ruft der IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> Kontextanbieter benachrichtigen, dass der kontextbehälter aktualisiert wird. Verwenden Sie diesen Aufruf, um die Attribute und Schlüsselwörter in der kontextbehälter und alle Sammlungen Unterkontext geändert, bevor die **Dynamische Hilfe** Fenster Update auftritt.  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> auf die kontextbehälter, um anzugeben, dass der Editor oder Designer neuen Kontext.  
  
     Wenn die **Dynamische Hilfe** Fenster Aufrufe <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> an, dass er aktualisiert wird, Editor oder Designer aktualisiert den Kontext für die übergeordnete kontextbehälter und alle Sammlungen Unterkontext zu diesem Zeitpunkt.  
  
    > [!NOTE]
    >  Die `SetDirty` Flag ist auf automatisch eingestellt `true` immer Kontext hinzugefügt oder entfernt Sie aus der Kontextsammlung. Die **Dynamische Hilfe** Fenster ruft nur <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> auf die kontextbehälter Wenn das `SetDirty` Flag festgelegt ist `true`. Er wird zurückgesetzt, um `false` nach der Aktualisierung.  
  
3.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> um die Auflistung der aktiven Kontext Kontext hinzuzufügen oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> Kontext zu entfernen.  
  
## Robuste Programmierung  
 Wenn Sie einen eigenen Editor schreiben, müssen Sie alle drei der Verfahren in diesem Thema Bereitstellen von Kontext für den Editor abschließen.  
  
> [!NOTE]
>  Ein Editor oder Designer\-Fenster ordnungsgemäß zu aktivieren und sicherzustellen, dass Befehlsrouting ordnungsgemäß aktualisiert wird, müssen Sie aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> auf die Komponente, die das Fokusfenster zu erleichtern.  
  
 Die SEID ist eine Auflistung von Eigenschaften, die sich ändern, die basierend auf der Auswahl. SEID Informationen sind über die globale Auswahl zur Verfügung. Die globale Auswahl in von ausgelöste Ereignisse wired ist die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> \-Schnittstelle, und eine Liste aller Elemente, die ausgewählt \(aktuelle\-Editor, aktuelle Toolfenster, aktuellen Hierarchie usw.\).  
  
 Für Editoren und Designern in welchem Kontext immer ändern kann verschiebt der Cursor innerhalb eines Worts kontextbehälter aktualisiert ineffizient ist. Um die Aktualisierung effizienter jederzeit Sie erkennen, dass den Cursor im Editor oder Designer\-Fenster verschieben, rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>. Auf diese Weise können Sie zum Speichern der Gerätekontext ändert sich, bis es Leerlaufzeit und die IDE Kontext Service Benachrichtigung für den Editor oder Designer sendet, den **Dynamische Hilfe** Fenster wird aktualisiert. Dieser Ansatz wird im Verfahren "So verwalten die Kontextsammlung" in diesem Thema verwendet.  
  
 Nach dem Kontext für Aktivitäten in Ihrem Editor oder Designer bereitstellen, sollten Sie ein bestimmtes F1\-Schlüsselwort, damit Benutzer die Hilfe für den Editor oder Designer selbst können bereitstellen.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>