---
title: "Ereignishandler Weitergeben von Änderungen außerhalb des Modells | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 717f61f440414370f3e9a2180e1c1cade7436aeb
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Ereignishandler propagieren Änderungen außerhalb des Modells
In Visualization and Modeling SDK, definieren Sie Store-Ereignishandler, um die Weitergabe von Änderungen auf Ressourcen außerhalb des Informationsspeichers, z. B. keine Store-Variablen, Dateien, im anderen Speicher oder anderen Modellen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterungen. Store-Ereignishandler werden nach dem Ende der Transaktion ausgeführt, in denen die auslösende Ereignis aufgetreten ist. Sie werden auch in einem Vorgang rückgängig gemacht bzw. wiederholt ausgeführt werden. Aus diesem Grund sind im Gegensatz zum Speicher-Regeln Speicherereignisse besten zum Aktualisieren von Werten, die sich außerhalb des Informationsspeichers befinden. Im Gegensatz zu .NET Ereignisse, Ereignishandler Store Lauschen auf eine Klasse registriert sind: Sie müssen nicht für jede Instanz einen separaten Handler registriert werden soll. Weitere Informationen zur Wahl zwischen verschiedenen Methoden zum Behandeln der Änderungen, finden Sie unter [Weitergeben von Änderungen und reagieren auf](../modeling/responding-to-and-propagating-changes.md).  
  
 Die grafische Oberfläche und andere Steuerelemente der Benutzeroberfläche sind Beispiele für externe Ressourcen, die vom Store Ereignisse verarbeitet werden können.  
  
### <a name="to-define-a-store-event"></a>So definieren Sie eine Store-Ereignis  
  
1.  Wählen Sie den Typ des Ereignisses, das Sie überwachen möchten. Eine vollständige Liste finden Sie in den Eigenschaften des <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>. Jede Eigenschaft entspricht ein Ereignistyp. Häufig verwendete die letzte Ereignis-Typen sind:  
  
    -   `ElementAdded`-ausgelöst, wenn ein Modellelement, Beziehungslink, Form oder den Verbinder erstellt.  
  
    -   ElementPropertyChanged - ausgelöst, wenn der Wert des einem `Normal` Eigenschaft "Domain" geändert wird. Das Ereignis wird ausgelöst, nur, wenn die alten und neuen Werte nicht gleich sind. Das Ereignis kann nicht auf berechnete und benutzerdefinierte Speichereigenschaften angewendet werden.  
  
         Es kann nicht an den Rolleneigenschaften angewendet werden, die beziehungslinks entsprechen. Verwenden Sie stattdessen `ElementAdded` die domänenbeziehung überwachen.  
  
    -   `ElementDeleted`– nach einem Modellelement ausgelöst, Beziehung, Form oder Connector gelöscht wurde. Die Eigenschaftswerte des Elements können Sie weiterhin zugreifen, aber sie weist keine Beziehungen zu anderen Elementen.  
  
2.  Hinzufügen eine partiellen Klassendefinition für *YourDsl *** DocData** in einer separaten Codedatei in der **DslPackage** Projekt.  
  
3.  Schreiben Sie den Code des Ereignisses als eine Methode, wie im folgenden Beispiel gezeigt. Es kann sein `static`, es sei denn, Sie möchten den Zugriff auf `DocData`.  
  
4.  Überschreiben Sie `OnDocumentLoaded()` Handler registriert werden. Wenn Sie mehrere Handler verfügen, können Sie diese an demselben Ort registrieren.  
  
 Der Speicherort des Registrierungscodes ist nicht wichtig. `DocView.LoadView()`wird von ein anderen Speicherort.  
  
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
      base.OnDocumentLoaded(); // Don't forget this.  
  
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
  
## <a name="using-events-to-make-undoable-adjustments-in-the-store"></a>Verwenden von Ereignissen zu machende Anpassungen im Speicher  
 Store-Ereignisse werden nicht normal verwendet für die Weitergabe von Änderungen in den Speicher, da der Ereignishandler ausgeführt wird, nachdem die Transaktion ein Commit ausgeführt wird. Stattdessen verwenden Sie eine Store-Regel. Weitere Informationen finden Sie unter [weitergeben Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Jedoch, können Sie einen Ereignishandler verwenden, zusätzliche Updates in den Speicher vorzunehmen, wenn der Benutzer auf die zusätzlichen Updates separat aus dem ursprünglichen Ereignis rückgängig gemacht werden soll. Nehmen wir beispielsweise an, dass Kleinbuchstaben der üblichen Konvention für Albumtiteln sind. Einen Ereignishandler für den Speicher geschrieben, der den Titel in Kleinbuchstaben korrigiert, nachdem der Benutzer in Großbuchstaben eingegeben wurde. Aber der Benutzer konnte mit dem Befehl "Rückgängig" verwendet, um Ihre Korrektur "Abbrechen", die Großbuchstaben wiederherstellen. Eine zweite rückgängig machen würden die Änderung des Benutzers entfernt werden.  
  
 Im Gegensatz dazu, wenn Sie eine Store-Regel, um die Ausführung geschrieben haben, wäre des Benutzers ändern und Ihre Korrektur in der gleichen Transaktion, damit der Benutzer die Anpassung ohne Verlust der ursprünglichen Änderung nicht rückgängig konnte.  
  
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
  
 Wenn Sie ein Ereignis, die die Speicher aktualisiert schreiben:  
  
-   Verwendung `store.InUndoRedoOrRollback` zu vermeiden, dass Änderungen mit Modellelementen im rückgängig. Der Transaktions-Manager wird alles, was in den Speicher wieder in seinen ursprünglichen Zustand festgelegt.  
  
-   Verwendung `store.InSerializationTransaction` vermeiden Sie Änderungen vornehmen, während das Modell aus der Datei geladen wird.  
  
-   Ihre Änderungen führen weitere Ereignisse ausgelöst werden soll. Stellen Sie sicher, dass Sie eine unendliche Schleife vermeiden.  
  
## <a name="store-event-types"></a>Speichern von Ereignistypen  
 Jedes Ereignis des Typs entspricht einer Auflistung in Store.EventManagerDirectory. Können Sie hinzufügen oder Entfernen von Ereignishandlern zu einem beliebigen Zeitpunkt, aber es ist üblich, die sie hinzufügen, wenn das Dokument geladen wird.  
  
|`EventManagerDirectory`Eigenschaftenname|Wann ausgeführt|  
|-------------------------------------------|-------------------|  
|ElementAdded|Eine Instanz einer Domänenklasse, domänenbeziehung, Form, Connector oder Diagramm wird erstellt.|  
|ElementDeleted|Ein Modellelement wurde aus dem Store Element Verzeichnis entfernt und ist nicht mehr die Quelle oder das Ziel jeder Beziehung. Das Element wird nicht tatsächlich aus dem Arbeitsspeicher gelöscht, aber bei einem zukünftigen rückgängig beibehalten wird.|  
|ElementEventsBegun|Am Ende einer äußeren Transaktion aufgerufen.|  
|ElementEventsEnded|Wird aufgerufen, wenn alle anderen Ereignisse verarbeitet wurden.|  
|ElementMoved|Ein Modellelement wurde aus einem Store Partition in eine andere verschoben.<br /><br /> Dies bezieht sich nicht auf den Speicherort einer Form im Diagramm.|  
|ElementPropertyChanged|Der Wert der Eigenschaft "Domain" eine wurde geändert. Dies ist nur ausgeführt, wenn die alten und neuen Werte ungleich sind.|  
|RolePlayerChanged|Einer der zwei Rollen (enden) einer Beziehung verweist auf ein neues Element.|  
|RolePlayerOrderChanged|In einer Rolle mit einer Multiplizität größer als 1 ist ist die Abfolge der Links geändert.|  
|TransactionBeginning||  
|TransactionCommitted||  
|TransactionRolledBack||  
  
## <a name="see-also"></a>Siehe auch  
 [Reagieren auf und das Weitergeben von Änderungen](../modeling/responding-to-and-propagating-changes.md)   
 [Beispielcode: Schaltpläne](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 
