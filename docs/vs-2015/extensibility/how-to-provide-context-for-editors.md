---
title: 'Gewusst wie: Bereitstellen von Kontext für Editoren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 11a98599a9812cd00650d113170ff55c01ac44db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841002"
---
# <a name="how-to-provide-context-for-editors"></a>Vorgehensweise: Angeben von Kontext für Editoren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bei einem Editor ist der Kontext nur aktiv, wenn der Editor den Fokus besitzt oder unmittelbar vor dem Verschieben des Fokus in ein Tool Fenster den Fokus hatte. Sie können einen Kontext für einen Editor bereitstellen, indem Sie die folgenden Schritte ausführen:  
  
1. Erstellen Sie einen Kontext Behälter.  
  
2. Veröffentlichen Sie den Kontext Behälter in der Auswahl Element Kennung (seid).  
  
3. Behält den Kontext in der Sammlung bei.  
  
   Diese Aufgaben werden in den folgenden Verfahren behandelt. Weitere Informationen zum Bereitstellen von Kontext finden Sie unter **robuste Programmierung** weiter unten in diesem Thema.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>So erstellen Sie einen Kontext Behälter für einen Editor oder Designer  
  
1. Ruft `QueryService` <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> für die-Schnittstelle für den <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> Dienst auf.  
  
     Ein Zeiger auf die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> Schnittstelle wird zurückgegeben.  
  
2. Rufen Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> Methode auf, um einen neuen Kontext oder einen unter Kontext Behälter zu erstellen.  
  
     Ein Zeiger auf die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> Schnittstelle wird zurückgegeben.  
  
3. Aufrufen der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> Methode zum Hinzufügen von Attributen, Such Schlüsselwörtern oder F1-Schlüsselwörtern zum Kontext-oder unter Kontext Behälter.  
  
4. Wenn Sie einen unter Kontext Behälter erstellen, wird die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> Methode aufgerufen, um den unter Kontext Behälter mit dem übergeordneten Kontext Behälter zu verknüpfen.  
  
5. Ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> auf, um eine Benachrichtigung zu erhalten, wenn das **Dynamische Hilfe** Fenster gerade aktualisiert wird.  
  
     Wenn Sie das Fenster " **Dynamische Hilfe** " aufrufen, um den Editor aufzurufen, wenn er bereit für die Aktualisierung ist, haben Sie die Möglichkeit, den Kontext bis zum Update zu ändern. Dies kann die Leistung verbessern, da die Ausführung zeitaufwendiger Algorithmen verzögert werden kann, bis die Leerlaufzeit des Systems zur Verfügung steht.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>So veröffentlichen Sie den Kontext Behälter in den seid  
  
1. Ruft für `QueryService` den <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> Dienst auf, um einen Zeiger auf die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> Schnittstelle zurückzugeben.  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>Geben Sie an, und geben Sie einen Element Bezeichner ( `elementid` Parameter) SEID_UserContext an, um anzugeben, dass Sie den Kontext an die globale Ebene übergeben.  
  
3. Wenn der Editor oder Designer aktiv wird, werden die Werte in seinem <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> Objekt an die globale Auswahl weitergegeben. Sie müssen diesen Vorgang nur einmal pro Sitzung ausführen und dann den Zeiger auf den globalen Kontext speichern, den Sie beim Aufrufen von erstellt haben <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> .  
  
### <a name="to-maintain-the-context-bag"></a>So behalten Sie den Kontext Behälter bei  
  
1. Implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> , um sicherzustellen, dass das **Dynamische Hilfe** Fenster den Editor oder Designer aufruft, bevor es aktualisiert wird.  
  
     Für jeden Kontext Behälter, der aufgerufen wurde, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> nachdem der Kontext Behälter erstellt und implementiert wurde <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> , ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> auf, um den Kontext Anbieter zu benachrichtigen, dass der Kontext Behälter aktualisiert wird. Sie können diesen Befehl verwenden, um die Attribute und Schlüsselwörter im Kontext Behälter und in allen unter Kontext-Säcken zu ändern, bevor das **Dynamische Hilfe** Fenster aktualisiert wird.  
  
2. Ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> für den Kontext Behälter auf, um anzugeben, dass der Editor oder Designer über einen neuen Kontext verfügt.  
  
     Wenn das **Dynamische Hilfe** Fenster aufruft, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> um anzugeben, dass es aktualisiert wird, kann der Editor oder Designer den Kontext für den übergeordneten Kontext Behälter und alle unter Kontext Behälter zu diesem Zeitpunkt entsprechend aktualisieren.  
  
    > [!NOTE]
    > Das- `SetDirty` Flag wird automatisch auf festgelegt, `true` Wenn der Kontext Behälter dem Kontext hinzugefügt oder daraus entfernt wird. Das **Dynamische Hilfe** Fenster ruft nur <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> im Kontext Behälter auf, wenn das- `SetDirty` Flag auf festgelegt ist `true` . Sie wird `false` nach dem Update auf zurückgesetzt.  
  
3. Ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> auf, um der aktiven Kontext Auflistung Kontext hinzuzufügen oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> um den Kontext zu entfernen.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Wenn Sie einen eigenen Editor schreiben, müssen Sie alle drei Prozeduren in diesem Thema ausführen, um den Kontext für den Editor bereitzustellen.  
  
> [!NOTE]
> Wenn Sie einen Editor oder ein Designer Fenster ordnungsgemäß aktivieren und sicherstellen möchten, dass die Befehls Weiterleitung ordnungsgemäß aktualisiert wird, müssen Sie für die-Komponente aufzurufen, damit <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> Sie das Fokus Fenster wird  
  
 Das seid ist eine Auflistung von Eigenschaften, die sich basierend auf der Auswahl ändern. SEID-Informationen sind über die globale Auswahl verfügbar. Die globale Auswahl wird in Ereignisse eingebunden, die von der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> Schnittstelle ausgelöst werden, und verfügt über eine Liste aller ausgewählten Elemente (aktueller Editor, Aktuelles Tool Fenster, aktuelle Hierarchie usw.).  
  
 Wenn sich der Cursor innerhalb eines Worts bewegt, ist es für Editoren und Designer nicht ineffizient, den Kontext Behälter ständig zu aktualisieren, wenn sich der Cursor innerhalb eines Worts bewegen kann. Um das Update effizienter zu gestalten, wenn Sie den Cursor innerhalb des Editors oder des Designer Fensters erkennen, können Sie den Aufruf von durchführen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> . Auf diese Weise können Sie die Kontext Änderungen speichern, bis eine Leerlaufzeit vorhanden ist, und der Kontext Dienst der IDE sendet eine Benachrichtigung an den Editor oder Designer, den das **Dynamische Hilfe** Fenster aktualisiert. Diese Vorgehensweise wird im Verfahren "so behalten Sie den Kontext Behälter" in diesem Thema verwendet.  
  
 Nachdem Sie Kontext für Aktivitäten in Ihrem Editor oder Designer bereitgestellt haben, sollten Sie ein bestimmtes F1-Schlüsselwort bereitstellen, um Benutzern die Möglichkeit zu geben, Hilfe für den Editor oder Designer zu erhalten.  
  
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
