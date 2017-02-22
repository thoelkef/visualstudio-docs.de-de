---
title: "Ereignishandler propagieren &#196;nderungen au&#223;erhalb des Modells | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Ereignisse"
  - "Domänenspezifische Sprache, Programmierdomänenmodelle"
ms.assetid: 0ac8d1e4-239f-4370-ba1d-3769bb38b8a5
caps.latest.revision: 18
caps.handback.revision: 18
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Ereignishandler propagieren &#196;nderungen au&#223;erhalb des Modells
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In Visualisierung und Modellieren SDK können Sie Ereignishandler für die Speicherung definieren, um Änderungen an Ressourcen außerhalb des Arbeitsspeichers, z. B. Nicht Speicher Variablen verbreitet werden soll, in anderen Dateien speichert Modelle oder andere [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterungen.  Ereignishandler für die Speicherung werden nach dem Ende der Transaktion ausgeführt, in der die startende Ereignis aufgetreten ist.  Sie werden auch in einem Rückgängig\- oder einem Wiederholungsvorgang ausgeführt.  Daher Speicher unterschiedlich sind Regeln zum Speichern von Ereignissen zum Aktualisieren der Werte sehr nützlich, die sich außerhalb des Arbeitsspeichers sind.  Im Gegensatz zu .NET\-Ereignisse registrierten Ereignishandler für die Speicherung werden, um zu einer Klasse zu überwachen: Sie müssen einen separaten Handler für jede Instanz nicht registrieren.  Weitere Informationen dazu, wie Sie zwischen verschiedenen Möglichkeiten, Änderungen zu behandeln, finden Sie unter [Reagieren auf und Propagieren von Änderungen](../modeling/responding-to-and-propagating-changes.md)auswählt.  
  
 Die grafische Oberfläche und andere Steuerelemente der Benutzeroberfläche sind Beispiele für externe Ressourcen, die vom Speicher von Ereignissen behandelt werden können.  
  
### So definieren Sie ein Speicher für Auswahlereignisse  
  
1.  Wählen Sie den Typ des Ereignisses aus, den Sie überwachen möchten.  Eine vollständige Liste der Eigenschaften von Betrachten Sie <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>.  Jede Eigenschaft entspricht einem Ereignistyp.  Die am häufigsten verwendeten Ereignistypen sind:  
  
    -   `ElementAdded` – ausgelöst, wenn ein Modellelement ein Verhältnis\-Link, eine Form oder ein Konnektor erstellt wird.  
  
    -   ElementPropertyChanged – ausgelöst, wenn sich der Wert einer `Normal` Domäneneigenschaft geändert wird.  Das Ereignis wird nur ausgelöst, wenn die alten und neuen Werte ungleich sind.  Das Ereignis kann nicht in den berechneten und benutzerdefinierten Speicherung von Eigenschaften angewendet werden.  
  
         Sie kann nicht zur Rolle Eigenschaft angewendet werden, die den Verhältnis\-Links entsprechen.  Verwenden Sie stattdessen `ElementAdded` , das Domänen\-Verhältnis zu überwachen.  
  
    -   –`ElementDeleted` nach einem Modellelement gestartet wird, ist der Beziehung, Form oder Konnektor gelöscht.  Sie können die Eigenschaftswerte des Elements zugreifen, jedoch keine Beziehungen zu anderen Elementen.  
  
2.  Fügen Sie eine partielle Klassendefinition für *TheDsl***DocData** in einer separaten Codedatei im **DslPackage** Projekt hinzu.  
  
3.  Schreiben Sie den Code des Ereignisses als Methode, wie im folgenden Beispiel veranschaulicht.  Es kann `static`sein, es sei denn, Sie `DocData`zugreifen möchten.  
  
4.  Überschreiben `OnDocumentLoaded()` , für das der Handler registriert werden soll.  Wenn Sie mehr als einen Handler haben, können Sie diese alle im gleichen Position registrieren.  
  
 Der Speicherort des Codes Registrierung ist nicht wichtig.  `DocView.LoadView()` ist ein alternativer Speicherort.  
  
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
  
## Verwenden von Ereignissen, um Anpassungen vornehmen Undoable im Speicher  
 Speicherung von Ereignissen sind nicht in der Regel zur Weitergabe von Änderungen im Speicher verwendet, da der Ereignishandler ausgeführt werden, nachdem ein Commit für die Transaktion ausgeführt wird.  Stattdessen müssen Sie die Regel eine Speicherung verwenden.  Weitere Informationen finden Sie unter [Regeln propagieren Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Allerdings können Sie einen Ereignishandler verwenden, um zusätzliche Updates im Speicher auszuführen, wenn der Benutzer in der Lage sein sollen, zusätzliche Aktualisierungen unabhängig vom ursprünglichen rückgängig zu machen.  Angenommen, Kleinbuchstaben die übliche Konvention für Album Namen sind.  Sie können einen Speicher Ereignishandler schreiben, der den Namen in Kleinbuchstaben festgelegt, nachdem der Benutzer in Großbuchstaben eingegeben hat.  Wenn der Benutzer kann den Befehl Rückgängig verwenden, die Korrektur abzubrechen und die Großbuchstaben wiederherstellen.  Zweites Undo würde die Änderung des Benutzers entfernen.  
  
 Im Gegensatz dazu wenn Sie eine Speicherung die Regel geschrieben haben, die dasselbe Ziel zu erreichen, wird die Änderung des Benutzers und die Korrektur in der gleichen Transaktion ausgeführt werden, damit der Benutzer die Anpassung konnte nicht rückgängig machen, ohne die ursprüngliche Änderung zu verlieren.  
  
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
  
 Wenn Sie ein Ereignis schreiben, das den Speicher aktualisiert:  
  
-   Verwendung `store.InUndoRedoOrRollback` Änderungen an Modellelemente in rückgängig macht vornehmen zu vermeiden.  Der Transaktions\-Manager legt alle im Speicher zurück auf den ursprünglichen Zustand fest.  
  
-   Verwendung `store.InSerializationTransaction` Änderungen vornehmen zu müssen, während das Modell der Datei geladen wird.  
  
-   Die Änderungen verursachen weitere Ereignisse ausgelöst werden.  Stellen Sie sicher, dass Sie eine Endlosschleife vermeiden.  
  
## Speicher\-Ereignistypen  
 Jeder Ereignistyp entspricht einer Auflistung in Store.EventManagerDirectory.  Sie können jederzeit Ereignishandler hinzufügen oder entfernen, ist jedoch üblich, der hinzugefügt werden soll, wenn das Dokument geladen wird.  
  
|`EventManagerDirectory`\-Eigenschaftenname|Wenn Ausgeführt|  
|------------------------------------------------|---------------------|  
|ElementAdded|Eine Instanz einer Domänenklasse, Domänen\-Verhältnisses, der Form des Konnektors oder eines Diagramms wird erstellt.|  
|ElementDeleted|Ein Modellelement wurde vom Element entfernt Verzeichnis des Speichers und ist nicht mehr die Quelle oder das Ziel jeder Beziehung.  Das Element wird nicht tatsächlich aus dem Speicher gelöscht, aber wird im Falle der Zukunft rückgängig machen beibehalten.|  
|ElementEventsBegun|Wird am Ende einer äußeren Transaktion.|  
|ElementEventsEnded|Wird aufgerufen, wenn alle anderen Ereignisse verarbeitet wurden.|  
|ElementMoved|Ein Modellelement wurde über eine Speicherung partition in einen anderen verschoben.<br /><br /> Dies wird nicht in den Speicherort einer Form im Diagramm verknüpft.|  
|ElementPropertyChanged|Der Wert einer Domäneneigenschaft hat sich geändert.  Dies wird nur ausgeführt, wenn die alten und neuen Werte ungleich sind.|  
|RolePlayerChanged|Eine der zwei Rollen \(Enden\) einer Beziehung verweist auf ein neues Element.|  
|RolePlayerOrderChanged|In einer Rolle mit einer Multiplizität größer als 1 ist, wird die Sequenz von Links geändert.|  
|TransactionBeginning||  
|TransactionCommitted||  
|TransactionRolledBack||  
  
## Siehe auch  
 [Reagieren auf und Propagieren von Änderungen](../modeling/responding-to-and-propagating-changes.md)   
 [Sample code: Circuit Diagrams](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)