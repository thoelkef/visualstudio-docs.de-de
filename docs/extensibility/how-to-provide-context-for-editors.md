---
title: 'Vorgehensweise: Bereitstellen von Kontext für Editoren | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0adc498ebaaf7ea1b5de033d4d589d99545da976
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068235"
---
# <a name="how-to-provide-context-for-editors"></a>Vorgehensweise: Bereitstellen von Kontext für Editoren
Der Kontext ist für einen Editor aktiv, nur, wenn der Editor den Fokus besitzt, oder vor der Fokus sofort der Fokus zu einem Toolfenster verschoben wurde. Sie können den Kontext für einen Editor angeben, indem Sie die folgenden Aufgaben:

1. Erstellen Sie eine Kontextsammlung.

2. Veröffentlichen Sie die Kontextsammlung auf die Auswahl-Element-ID (SEID).

3. Behalten Sie den Kontext im Behälter.

   Diese Aufgaben fallen unter den folgenden Verfahren. Weitere Informationen zum Bereitstellen von Kontext finden Sie unter **Robuste Programmierung** weiter unten in diesem Artikel.

## <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Um eine Kontextsammlung für einen Editor oder Designer zu erstellen.

1. Rufen Sie `QueryService` auf Ihre <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> eine Schnittstelle für die <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> Service.

     Ein Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> -Schnittstelle wird zurückgegeben.

2. Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> Methode, um einen neuen Kontext oder unterkontextbehälter Behälter zu erstellen.

     Ein Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> -Schnittstelle wird zurückgegeben.

3. Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> Methode zum Hinzufügen von Attributen, Suche nach Schlüsselwörtern oder **F1** Schlüsselwörter aufgelistet, die Kontext-oder unterkontextbehälter.

4. Wenn Sie eine unterkontextsammlung erstellen, rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> Methode, um den unterkontextbehälter mit der übergeordneten Kontextsammlung verknüpft.

5. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> benachrichtigt bei der **dynamische Hilfe** Fenster ist, zu aktualisieren.

     Mit der **dynamische Hilfe** Fenster rufen Sie den Editor bereit zum Aktualisieren von wird er bietet Ihnen die Möglichkeit, verzögern, ändern den Kontext, bis das Update auftritt. Auf diese Weise kann die Leistung verbessern, da dadurch zu verzögern, zeitaufwändige Algorithmen ausgeführt, bis System-Leerlaufzeit verfügbar ist.

## <a name="to-publish-the-context-bag-to-the-seid"></a>Die Kontextsammlung auf die SEID veröffentlichen

1. Rufen Sie `QueryService` auf die <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> Dienst zur Rückgabe eines Zeigers auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> Schnittstelle.

2. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, einen Elementbezeichner angeben (`elementid` Parameter) Wert SEID_UserContext, um anzugeben, dass Sie bis zur globalen Ebene Kontext übergeben.

3. Wenn der Editor oder Designer aktiviert wird, die Werte in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> Objekt an die globale Auswahl weitergegeben werden. Sie müssen nur dieser Prozess einmal pro Sitzung abgeschlossen, und speichern Sie den Zeiger auf den globalen Kontext erstellt, wenn Sie aufgerufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.

## <a name="to-maintain-the-context-bag"></a>Um den kontextbehälter zu verwalten.

1. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> um sicherzustellen, dass die **dynamische Hilfe** Fenster Editor oder Designer aufgerufen, bevor sie aktualisiert.

     Für jede Kontextsammlung, die aufgerufen wird, verfügt über <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> nach der kontextbehälter erstellt wird und implementiert hat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, die IDE-Aufrufe <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> , dem Kontextanbieter benachrichtigen, dass es sich bei der kontextbehälter aktualisiert werden. Können Sie diesen Aufruf so ändern Sie die Attribute und Schlüsselwörter, die in den kontextbehälter und alle unterkontextbehälter, bevor die **dynamische Hilfe** fensterupdate auftritt.

2. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> auf den kontextbehälter, um anzugeben, dass Editor oder Designer der neuen Kontext aus.

     Wenn die **dynamische Hilfe** Fenster Aufrufe <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> , um anzugeben, dass es aktualisiert, Editor oder Designer aktualisiert den Kontext entsprechend der übergeordneten Kontextsammlung sowohl für alle unterkontextbehälter zu diesem Zeitpunkt.

    > [!NOTE]
    >  Die `SetDirty` Kennzeichen auf automatisch eingestellt ist `true` jedes Mal, wenn Kontext hinzugefügt oder entfernt Sie aus dem kontextbehälter. Die **dynamische Hilfe** Fenster nur Aufrufe <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> auf den kontextbehälter Wenn die `SetDirty` ergebniskennzeichen auf `true`. Er wird zurückgesetzt, um `false` nach dem Update.

3. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> , um die Sammlung von aktiven Kontext Kontext hinzuzufügen oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> Kontext zu entfernen.

## <a name="robust-programming"></a>Stabile Programmierung
 Wenn Sie Ihren eigenen Editor schreiben, müssen Sie alle drei der Verfahren in diesem Artikel, um den Kontext für den Editor bieten abschließen.

> [!NOTE]
>  Um ein Editor oder Designer-Fenster ordnungsgemäß zu aktivieren und stellen Sie sicher, dass das Befehlsrouting ordnungsgemäß aktualisiert wird, müssen Sie aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> auf die Komponente, für das Fokusfenster zu erleichtern.

 Die SEID ist eine Auflistung von Eigenschaften, die sich ändern, die basierend auf der Auswahl. SEID Informationen sind über die globale Auswahl zur Verfügung. Die globale Auswahl ist in von ausgelöste Ereignisse verknüpft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> -Schnittstelle, und hat eine Liste aller Elemente, die ausgewählt werden, (aktuellen-Editor, aktuellen Toolfensters, aktuellen Hierarchie und So weiter).

 Für Editoren und Designern in welchem Kontext bei jedem ändern kann der Cursor springt innerhalb eines Worts, sehr aufwändig, ständig den kontextbehälter zu aktualisieren ist. Damit aktualisieren eine effizientere jedes Mal, die Sie erkennen, dass den Cursor im Editor oder Designer-Fenster verschoben wird, können Sie aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>. Dies ermöglicht es Ihnen, um die kontextänderungen zu speichern, bis es Zeit im Leerlauf ist und der IDE-Kontext-Dienst Benachrichtigung für den Editor oder Designer, die sendet die **dynamische Hilfe** Fenster wird aktualisiert. Dieser Ansatz wird verwendet, der **darin den kontextbehälter** in diesem Artikel.

 Nachdem Sie Kontext für Aktivitäten in Ihrem Editor oder Designer haben, sollten Sie eine bestimmte bereitstellen **F1** Schlüsselwort, um Benutzern das Abrufen von Hilfe für den Editor oder Designer selbst ermöglichen.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>