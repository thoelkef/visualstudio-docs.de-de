---
title: Ereignishandler propagieren Änderungen außerhalb des Modells | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
ms.assetid: 0ac8d1e4-239f-4370-ba1d-3769bb38b8a5
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 38958aae1c2449145107faa7abe00a2d86baaa9a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303198"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Ereignishandler propagieren Änderungen außerhalb des Modells
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können im Visualisierungs- und Modellierungs-SDK, Store-Ereignishandler zum Weitergeben von Änderungen an Ressourcen außerhalb des Speichers an, wie z. B. nicht über den Store-Variablen, die Dateien, die Modelle in anderen Datenspeichern oder andere definieren [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Erweiterungen. Store-Ereignishandler werden nach dem Ende der Transaktion ausgeführt, in denen das auslösende Ereignis aufgetreten ist. Sie werden auch in einem Vorgang zum Rückgängigmachen oder Wiederholen-Vorgang ausgeführt. Aus diesem Grund sind im Gegensatz zu Regeln für Store Speicherereignissen besonders hilfreich für das Aktualisieren der Werte, die außerhalb des Speichers. Im Gegensatz zu .NET Ereignissen, Store-Ereignishandler registriert sind, um eine Klasse zu überwachen: Sie müssen keinen separaten Handler für jede Instanz registrieren. Weitere Informationen zur Wahl zwischen verschiedenen Methoden zum Verarbeiten von Änderungen, finden Sie unter [reagieren auf und propagieren Änderungen](../modeling/responding-to-and-propagating-changes.md).  
  
 Die grafische Oberfläche und andere Steuerelemente der Benutzeroberfläche sind Beispiele von externen Ressourcen, die von Store-Ereignisse behandelt werden können.  
  
### <a name="to-define-a-store-event"></a>Um ein Speicherereignis definieren  
  
1.  Wählen Sie den Typ des Ereignisses, das Sie überwachen möchten. Eine vollständige Liste finden Sie in den Eigenschaften des <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>. Jede Eigenschaft entspricht ein Ereignistyp. Am häufigsten verwendeten häufig die Ereignis-Typen sind:  
  
    -   `ElementAdded` : wird ausgelöst, wenn ein Element des Modells, Beziehungslink "," Form "oder" Verbindung wird erstellt.  
  
    -   ElementPropertyChanged – ausgelöst, wenn der Wert des einem `Normal` Domäneneigenschaft geändert wird. Das Ereignis wird ausgelöst, nur dann, wenn die neuen und alten Werte nicht gleich sind. Das Ereignis kann nicht auf berechnete und benutzerdefinierte Speichereigenschaften angewendet werden.  
  
         Es kann nicht an den Rolleneigenschaften angewendet werden, die beziehungslinks entsprechen. Verwenden Sie stattdessen `ElementAdded` die domänenbeziehung zu überwachen.  
  
    -   `ElementDeleted` – nach einem Modellelement ausgelöst, Beziehung, eine Form oder Verbindung wurde gelöscht. Sie können weiterhin die Eigenschaftswerte des Elements zugreifen, aber es müssen keine Beziehungen zu anderen Elementen.  
  
2.  Fügen Sie eine partielle Klassendefinition für _Ihredsl_**DocData** in einer separaten Codedatei in die **DslPackage** Projekt.  
  
3.  Schreiben Sie den Code für das Ereignis als Methode, wie im folgenden Beispiel an. Es kann sein `static`, es sei denn, Sie möchten den Zugriff auf `DocData`.  
  
4.  Außer Kraft setzen `OnDocumentLoaded()` Handler registriert werden. Wenn Sie mehr als einen Handler verfügen, können Sie diese alle an derselben Stelle registrieren.  
  
 Der Speicherort des Registrierungscodes ist nicht wichtig. `DocView.LoadView()` ist ein alternativer Speicherort an.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  
  
namespace Company.MusicLib  
{  
  partial class MusicLibDocData  
  {  
    // Register store events here or in DocView.LoadView().  
    protected override void OnDocumentLoaded()  
    {  
      base.OnDocumentLoaded(); // Don’t forget this.  
  
      #region Store event handler registration.       
      Store store = this.Store;  
      EventManagerDirectory emd = store.EventManagerDirectory;  
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory  
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));  
      emd.ElementAdded.Add(linkInfo,   
          new EventHandler<ElementAddedEventArgs>(AddLink));  
      emd.ElementDeleted.Add(linkInfo,   
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));  
  
      #endregion Store event handlers.  
    }  
  
    private void AddLink(object sender, ElementAddedEventArgs e)  
    {  
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;  
      if (link != null)   
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);  
    }  
    private void RemoveLink(object sender, ElementDeletedEventArgs e)  
    {  
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;  
      if (link != null)   
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);  
    }  
  }  
  
}  
  
```  
  
## <a name="using-events-to-make-undoable-adjustments-in-the-store"></a>Verwenden von Ereignissen rückgängig gemacht werden Anpassungen vornehmen, in den Store  
 Store-Ereignisse werden nicht normalerweise verwendet für die Weitergabe von Änderungen in den Speicher, da der Ereignishandler ausgeführt wird, nachdem die Transaktion ein Commit ausgeführt wird. Stattdessen verwenden Sie eine Store-Regel. Weitere Informationen finden Sie unter [Regeln weitergegeben werden Änderungen in das Modell](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Allerdings können einen Ereignishandler Sie zusätzliche Updates an den Store vornehmen, wenn den Benutzer kann die zusätzlichen Updates separat aus dem ursprünglichen Ereignis rückgängig gemacht werden soll. Nehmen wir beispielsweise an, dass Kleinbuchstaben die übliche Konvention für Albumtiteln enthalten sind. Sie können einen Ereignishandler für den Speicher schreiben, der den Titel in Kleinbuchstaben korrigiert, nachdem der Benutzer in Großbuchstaben eingegeben hat. Aber der Benutzer kann den Befehl "Rückgängig" verwendet, um Ihre Korrekturen, Abbrechen der Großbuchstaben wiederherstellen. Rückgängig zu machen möchten, Entfernen des Benutzers ändern.  
  
 Im Gegensatz dazu, wenn Sie eine Store-Regel, um das gleiche tun geschrieben haben, wäre des Benutzers ändern und Ihre Korrekturen in der gleichen Transaktion, damit Benutzer nicht die Anpassung rückgängig machen konnte ohne Verlust der ursprünglichen Änderung.  
  
```  
  
partial class MusicLibDocView  
{  
    // Register store events here or in DocData.OnDocumentLoaded().  
    protected override void LoadView()  
    {  
      /* Register store event handler for Album Title property. */  
      // Get reflection data for property:  
      DomainPropertyInfo propertyInfo =   
        this.DocData.Store.DomainDataDirectory  
        .FindDomainProperty(Album.TitleDomainPropertyId);  
      // Add to property handler list:  
      this.DocData.Store.EventManagerDirectory  
        .ElementPropertyChanged.Add(propertyInfo,  
        new EventHandler<ElementPropertyChangedEventArgs>  
             (AlbumTitleAdjuster));  
  
      /*  
      // Alternatively, you can set one handler for   
      // all properties of a class.  
      // Your handler has to determine which property changed.  
      DomainClassInfo classInfo = this.Store.DomainDataDirectory  
           .FindDomainClass(typeof(Album));  
      this.Store.EventManagerDirectory  
          .ElementPropertyChanged.Add(classInfo,  
        new EventHandler<ElementPropertyChangedEventArgs>  
             (AlbumTitleAdjuster));  
       */  
      return base.LoadView();  
    }  
  
// Undoable adjustment after a property is changed.   
// Method can be static since no local access.  
private static void AlbumTitleAdjuster(object sender,  
         ElementPropertyChangedEventArgs e)  
{  
  Album album = e.ModelElement as Album;  
  Store store = album.Store;  
  
  // We mustn't update the store in an Undo:  
  if (store.InUndoRedoOrRollback   
      || store.InSerializationTransaction)  
      return;  
  
  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)  
  {  
    string newValue = (string)e.NewValue;  
    string lowerCase = newValue.ToLowerInvariant();  
    if (!newValue.Equals(lowerCase))  
    {  
      using (Transaction t = store.TransactionManager  
            .BeginTransaction("adjust album title"))  
      {  
        album.Title = lowerCase;  
        t.Commit();  
      } // Beware! This could trigger the event again.  
    }  
  }  
  // else other properties of this class.  
}  
  
```  
  
 Wenn Sie ein Ereignis, die den Speicher aktualisiert schreiben:  
  
-   Verwendung `store.InUndoRedoOrRollback` um zu vermeiden, Änderungen an Modellelemente in rückgängig. Der Transaktions-Manager wird alles, was in den Speicher wieder in den ursprünglichen Zustand festgelegt.  
  
-   Verwendung `store.InSerializationTransaction` um zu vermeiden, Änderungen vornehmen, während das Modell aus einer Datei geladen wird.  
  
-   Ihre Änderungen bewirkt Weitere Ereignisse ausgelöst werden. Stellen Sie sicher, dass Sie eine unendliche Schleife vermeiden.  
  
## <a name="store-event-types"></a>Store-Ereignistypen  
 Jeder Ereignistyp entspricht einer Auflistung in Store.EventManagerDirectory. Sie können das Hinzufügen oder Entfernen von Ereignishandlern zu einem beliebigen Zeitpunkt, aber es ist üblich, um sie hinzuzufügen, wenn das Dokument geladen wird.  
  
|`EventManagerDirectory` Eigenschaftenname|Ausgeführt, wenn|  
|-------------------------------------------|-------------------|  
|ElementAdded|Eine Instanz einer Domänenklasse, die domänenbeziehung, Form, Connector oder Diagramm wird erstellt.|  
|ElementDeleted|Ein Modellelement aus Element-Speicherverzeichnis entfernt wurde, und es ist nicht mehr, Quelle oder Ziel einer Beziehung. Das Element wird nicht tatsächlich aus dem Arbeitsspeicher gelöscht, aber bei einem zukünftigen rückgängig beibehalten wird.|  
|ElementEventsBegun|Am Ende einer äußeren Transaktion aufgerufen.|  
|ElementEventsEnded|Wird aufgerufen, wenn alle anderen Ereignisse verarbeitet wurden.|  
|ElementMoved|Ein Element des Modells wurde aus einem Speicher-Partition in eine andere verschoben.<br /><br /> Dies bezieht sich nicht auf den Speicherort einer Form im Diagramm.|  
|ElementPropertyChanged|Der Wert einer Domäneneigenschaft wurde geändert. Dies wird nur ausgeführt, wenn die alten und neuen Werte ungleich sind.|  
|RolePlayerChanged|Eine der zwei Rollen (enden) einer Beziehung verweist auf ein neues Element.|  
|RolePlayerOrderChanged|In einer Rolle mit der Multiplizität größer als 1 wurde die Abfolge von Links geändert.|  
|TransactionBeginning||  
|TransactionCommitted||  
|TransactionRolledBack||  
  
## <a name="see-also"></a>Siehe auch  
 [Reagieren auf und propagieren von Änderungen](../modeling/responding-to-and-propagating-changes.md)   
 [Beispielcode: Schaltpläne](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)



