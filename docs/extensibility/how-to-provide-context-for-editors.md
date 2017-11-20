---
title: "Vorgehensweise: Bereitstellen von Kontext für Editoren | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6687ce3ed73a96778b84cec6e77d5c0b3145702d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-context-for-editors"></a>Vorgehensweise: Bereitstellen von Kontext für Editoren
Der Kontext ist für einen Editor aktiv, nur, wenn der Editor den Fokus besitzt, oder den Fokus hat, unmittelbar vor dem Ausführen der Fokus auf ein Toolfenster verschoben wurde. Sie können den Kontext für einen Editor angeben, wie folgt:  
  
1.  Erstellen Sie eine Kontextsammlung.  
  
2.  Veröffentlichen Sie Behälter Kontext auf die Auswahl-Element-ID (SEID).  
  
3.  Behalten Sie den Kontext im Behälter.  
  
 Diese Aufgaben werden von den folgenden Prozeduren behandelt. Weitere Informationen zu den Kontext bereitstellt, finden Sie unter **Robuste Programmierung** weiter unten in diesem Thema.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>So erstellen Sie eine Kontextsammlung für einen Editor oder designer  
  
1.  Rufen Sie `QueryService` auf Ihre <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> eine Schnittstelle für die <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> Dienst.  
  
     Ein Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> -Schnittstelle wird zurückgegeben.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> Methode, um einen neuen Kontext oder Unterkontext Behälter zu erstellen.  
  
     Ein Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> -Schnittstelle wird zurückgegeben.  
  
3.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> -Methode zum Hinzufügen von Attributen, Lookup-Schlüsselwörter oder F1-Schlüsselwörter zum Kontext oder Unterkontext Behälter.  
  
4.  Wenn Sie eine Sammlung Unterkontext erstellen, rufen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> Methode Unterkontext Behälter mit übergeordneten Kontext Behälter zu verknüpfen.  
  
5.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> benachrichtigt werden soll bei der **dynamische Hilfe** Fenster aktualisiert wird.  
  
     Mit der **dynamische Hilfe** Fenster rufen Sie den Editor um aktualisieren wird er bietet Ihnen die Möglichkeit, den Kontext ändern, bis die Aktualisierung wird verzögert. Auf diese Weise kann die Leistung verbessern, da es Ihnen ermöglicht, verzögern zeitaufwändige Algorithmen ausgeführt, bis System Leerlaufzeit verfügbar ist.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>So veröffentlichen Sie Behälter Kontext auf die SEID  
  
1.  Rufen Sie `QueryService` auf die <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> Dienst zurückzugebenden einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> Schnittstelle.  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, geben Sie eine Element-ID (`elementid` Parameter) Wert des SEID_UserContext, um anzugeben, dass Sie den Kontext auf globaler Ebene übergeben.  
  
3.  Wenn der Editor bzw. Designer aktiviert wird, die Werte in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> Objekt der globalen Auswahl weitergegeben werden. Sie müssen nur zum Abschließen dieser einmal pro Sitzung, und speichern Sie den Mauszeiger an den globalen Kontext erstellt, wenn Sie aufgerufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.  
  
### <a name="to-maintain-the-context-bag"></a>Verwalten von Kontext Behälter  
  
1.  Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> um sicherzustellen, dass die **dynamische Hilfe** Fenster Editor oder Designer aufruft, bevor er aktualisiert.  
  
     Für jeden Kontext Behälter, die aufgerufen wird, hat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> nachdem Behälter Kontext erstellt und implementiert hat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> den Kontextanbieter benachrichtigen, dass der Behälter Kontext aktualisiert werden. Können Sie diesen Aufruf so ändern Sie die Attribute und Schlüsselwörter im Behälter Kontext und in alle Sammlungen Unterkontext vor der **dynamische Hilfe** Fenster Update ausgeführt.  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> auf Behälter Kontext, um anzugeben, dass der Editor bzw. Designer neuen Kontext verfügt.  
  
     Wenn die **dynamische Hilfe** Fenster Aufrufe <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> , um anzugeben, dass er aktualisiert, Editor oder Designer entsprechend für übergeordneten Kontext Behälter und alle Unterkontext aus diesem Kontext zu diesem Zeitpunkt aktualisiert.  
  
    > [!NOTE]
    >  Die `SetDirty` Flag ist auf automatisch festgelegt `true` bei jedem Kontext hinzugefügt oder daraus Kontext Behälter. Die **dynamische Hilfe** Fenster nur ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> auf Kontext Behälter Wenn die `SetDirty` Flag wird festgelegt, um `true`. Er wird zurückgesetzt, um `false` nach dem Update.  
  
3.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> Kontext auf die aktiven Kontext Auflistung hinzufügen oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> Kontext zu entfernen.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Wenn Sie Ihren eigenen Editor schreiben, müssen Sie alle drei der Verfahren in diesem Thema, um den Kontext für den Editor bieten abschließen.  
  
> [!NOTE]
>  Um ein Editor oder Designer-Fenster ordnungsgemäß zu aktivieren und stellen Sie sicher, dass das Befehlsrouting ordnungsgemäß aktualisiert wird, rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> auf die Komponente, für das Fokusfenster zu vereinfachen.  
  
 Die SEID ist eine Auflistung von Eigenschaften, die sich ändern, die basierend auf der Auswahl. SEID Informationen sind über die globale Auswahl zur Verfügung. Die globale Auswahl ist wired in Ereignissen ausgelöst werden, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> -Schnittstelle, und eine Liste aller Elemente, die ausgewählt (aktuellen Editor, aktuellen Toolfensters aktuellen Hierarchie und So weiter).  
  
 Für Editoren und Designern in welchem Kontext kann bei jedem ändern verschiebt der Cursor innerhalb eines Worts ist ineffizient, Kontext Behälter ständig zu aktualisieren. Um die Aktualisierung effizienter jederzeit Sie erkennen, dass den Cursor innerhalb der Editor bzw. Designer-Fenster verschieben, rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>. Auf diese Weise können Sie zum Speichern der Gerätekontext ändert sich erst im Leerlauf Zeit vorhanden ist, und die IDE Kontext Service Benachrichtigung in den Editor oder Designer, die sendet die **dynamische Hilfe** Fenster aktualisiert. Dieser Ansatz wird im Verfahren "So verwalten Kontext Behälter" in diesem Thema verwendet.  
  
 Nach dem Kontext für Aktivitäten in Ihren Editor oder Designer bereitstellt, sollten Sie ein bestimmtes F1-Schlüsselwort, um Benutzern das Abrufen von Hilfe zu dem Editor oder Designer selbst ermöglichen bereitstellen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>