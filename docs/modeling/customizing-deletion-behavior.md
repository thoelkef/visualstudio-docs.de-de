---
title: Anpassen des Verhaltens der Löschvorgang | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.deletebehavior
helpviewer_keywords:
- Domain-Specific Language, deletion
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 12f2a1690a4d68f6900006b10a699c23c83c8c2a
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2018
---
# <a name="customizing-deletion-behavior"></a>Anpassen des Löschverhaltens
Beim Löschen eines Elements werden normalerweise die verwandten Elemente ebenfalls gelöscht. Alle mit dem Element verbundenen Beziehungen und alle ihm untergeordneten Elemente werden gelöscht. Dieses Verhalten ist mit dem Namen *Löschweitergabe*. Sie können die Löschweitergabe anpassen, um beispielsweise zu veranlassen, dass zusätzliche verwandte Elemente gelöscht werden. Durch Schreiben von Programmcode können Sie die Löschweitergabe vom Zustand des Modells abhängig machen. Sie können auch andere Änderungen als Reaktion auf eine Löschung veranlassen.  
  
 Dieses Thema enthält die folgenden Abschnitte:  
  
-   [Löschen von Standardverhalten](#default)  
  
-   [Festlegen der Option weitergeben Löschen einer Rolle](#property)  
  
-   [Überschreiben die Schließung löschen](#closure) -verwenden Sie dieses Verfahren, in dem Löschen kann bis zum Löschen von benachbarten Elemente führen.  
  
-   [Verwenden von OnDeleting und OnDeleted](#ondeleting) -verwenden Sie diese Methoden, bei denen die Antwort andere Aktionen wie das Aktualisieren eines Wertes, entweder innerhalb oder außerhalb des Informationsspeichers enthalten kann.  
  
-   [Von Löschregeln](#rules) -Regeln Updates jeglicher Art in den Speicher weitergegeben, wenn eine Änderung an andere Personen führen möglicherweise zu verwenden.  
  
-   [Serverlöschereignisse](#rules) -Verwendung Speicherereignisse Updates außerhalb der Speicher, z. B. an andere weitergegeben [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Dokumente.  
  
-   [Zusammenführung aufheben](#unmerge) -mithilfe der Zusammenführung aufheben-Vorgangs können Sie um den Merge-Vorgang rückgängig zu machen, die ein untergeordnetes Element zum übergeordneten angefügt.  
  
##  <a name="default"></a> Löschen von Standardverhalten  
 Standardmäßig wird die Löschweitergabe durch folgende Regeln gesteuert:  
  
-   Beim Löschen eines Elements werden auch alle eingebetteten Elemente gelöscht. Die eingebetteten Elemente sind die Elemente, die Ziele einbettender Beziehungen sind, deren Quelle das Element darstellt. Angenommen, es besteht eine Einbetten von Beziehung aus **Album** auf **Musiktitel**, und klicken Sie dann bei einem bestimmten Album gelöscht wird, alle Titel ebenfalls gelöscht werden.  
  
     Im Gegensatz dazu wird beim Löschen eines Songs das Album nicht gelöscht.  
  
-   Die Löschung wird standardmäßig nicht über Verweisbeziehungen hinweg weitergegeben. Es ist eine verweisbeziehung **ArtistPlaysOnAlbum** aus **Album** zu **Interpreten**ein Album löschen alle zugehörigen Interpreten nicht gelöscht und durch das Löschen eines Interpreten nicht Löschen Sie alle Album.  
  
     Die Löschung wird jedoch über einige integrierte Beziehungen hinweg weitergegeben. Beispielsweise wird beim Löschen eines Modellelements auch seine Form im Diagramm gelöscht. Das Element und die Form sind durch die `PresentationViewsSubject`-Verweisbeziehung verbunden.  
  
-   Alle Beziehungen, die mit dem Element verbunden sind, sei es über die Quellrolle oder die Zielrolle, werden gelöscht. Die Rolleneigenschaft des Elements in der entgegengesetzten Rolle enthält das gelöschte Element nicht mehr.  
  
##  <a name="property"></a> Festlegen der Option weitergeben Löschen einer Rolle  
 Sie können die Weitergabe der Löschung entlang einer Verweisbeziehung oder von einem eingebetteten untergeordneten Element an sein übergeordnetes Element veranlassen.  
  
#### <a name="to-set-delete-propagation"></a>So legen Sie die Löschweitergabe fest  
  
1.  Wählen Sie auf der DSL-Definitionsdiagramm der *Rolle* , Weitergabe gelöscht werden soll. Die Rolle wird durch die Linie auf der linken oder rechten Seite eines Domänenbeziehungsfelds dargestellt.  
  
     Wenn Sie z. B. angeben möchten, dass beim Löschen eines Albums die zugehörigen Interpreten ebenfalls gelöscht werden, wählen Sie die Rolle aus, die mit der Domänenklasse "Interpret" verbunden ist.  
  
2.  Legen Sie im Fenster Eigenschaften die **weitergibt löschen** Eigenschaft.  
  
3.  Drücken Sie F5, und überprüfen Sie, ob Folgendes zutrifft:  
  
    -   Wird eine Instanz der Beziehung gelöscht, wird auch das Element in der ausgewählten Rolle gelöscht.  
  
    -   Wird ein Element in der entgegengesetzten Rolle gelöscht, werden Instanzen der Beziehung sowie die verwandten Elemente in dieser Rolle gelöscht.  
  
 Sie sehen auch die **weitergibt löschen** -Option in der **DSL-Detailfenster** Fenster. Wählen Sie eine Domänenklasse, und öffnen Sie in der DSL-Detailfenster der **Verhalten löschen** Seite, indem Sie auf die Schaltfläche auf der Seite des Fensters. Die **weitergeben** Option wird angezeigt, für die Rolle "entgegengesetzten" jeder Beziehung. Die **Stil löschen** Spalte gibt an, ob die **weitergeben** Option ist die Standardeinstellung, aber es muss kein separates unwirksam.  
  
## <a name="delete-propagation-by-using-program-code"></a>Löschweitergabe mithilfe von Programmcode  
 Über die Optionen in der DSL-Definitionsdatei können Sie nur wählen, ob die Löschung an einen unmittelbaren Nachbarn weitergegeben wird. Um ein komplexeres Schema für die Löschweitergabe zu implementieren, können Sie Programmcode schreiben.  
  
> [!NOTE]
>  Um Programmcode DSL-Definition hinzugefügt haben, erstellen Sie in eine separaten Codedatei der **Dsl** Projekt, und Schreiben von partiellen Definitionen, um die Klassen in den generierten Code Ordner zu erweitern. Weitere Informationen finden Sie unter [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
##  <a name="closure"></a> Definieren einen Delete-Abschluss  
 Der Löschvorgang verwendet die Klasse *YourModel***DeleteClosure** um zu bestimmen, welche Elemente zum Löschen angegebene eine erste Auswahl. `ShouldVisitRelationship()` und `ShouldVisitRolePlayer()` werden wiederholt aufgerufen, wobei das Diagramm der Beziehungen durchlaufen wird. Diese Methoden können Sie überschreiben. ShouldVisitRolePlayer wird mit der Identität des einen Link und das Element an einer der Rollen für den Link bereitgestellt. Es sollte einen der folgenden Werte zurückgeben:  
  
-   **VisitorFilterResult.Yes**: das Element gelöscht werden soll, und die Walker versuchen fortfahren sollte das Element des anderen Links.  
  
-   **VisitorFilterResult.DoNotCare** -das Element sollten nicht gelöscht werden, es sei denn, eine andere Abfrage antwortet, dass sie gelöscht werden soll.  
  
-   **VisitorFilterResult.Never** -Elements muss nicht gelöscht werden, auch wenn eine andere Abfrage Antworten **Ja**, und die Walker sollten nicht versuchen das Element des anderen Links.  
  
```  
// When a musician is deleted, delete their albums with a low rating.  
// Override methods in <YourDsl>DeleteClosure in DomainModel.cs  
partial class MusicLibDeleteClosure  
{  
  public override VisitorFilterResult ShouldVisitRolePlayer  
    (ElementWalker walker, ModelElement sourceElement, ElementLink elementLink,   
    DomainRoleInfo targetDomainRole, ModelElement targetRolePlayer)  
  {  
    ArtistAppearsInAlbum link = elementLink as ArtistAppearsInAlbum;  
    if (link != null   
       && targetDomainRole.RolePlayer.Id == Album.DomainClassId)  
    {  
      // Count other unvisited links to the Album of this link.  
      if (ArtistAppearsInAlbum.GetLinksToArtists(link.Album)  
              .Where(linkAlbumArtist =>   
                     linkAlbumArtist != link &&  
                     !walker.Visited(linkAlbumArtist))  
              .Count() == 0)  
      {  
        // Should delete this role player:  
        return VisitorFilterResult.Yes;   
      }  
      else  
        // Don't delete unless another relationship deletes it:  
        return VisitorFilterResult.DoNotCare;   
    }  
    else   
    {  
      // Test for and respond to other relationships and roles here.  
  
      // Not the relationship or role we're interested in.  
      return base.ShouldVisitRolePlayer(walker, sourceElement,   
             elementLink, targetDomainRole, targetRolePlayer);  
    }  
  }  
}  
  
```  
  
 Die Abschlusstechnik stellt sicher, dass die Menge der zu löschenden Elemente und Links bestimmt wird, bevor die Löschung beginnt. Der Walker kombiniert die Ergebnisse Ihres Abschlusses mit denen von anderen Modellteilen.  
  
 Die Technik setzt allerdings voraus, dass die Löschung nur die Nachbarn im Diagramm der Beziehungen betrifft: Sie können mit dieser Technik kein Element in einem anderen Teil des Modells löschen. Sie können sie nicht verwenden, wenn Sie auf eine Löschung hin Elemente hinzufügen oder andere Änderungen ausführen möchten.  
  
##  <a name="ondeleting"></a> Verwenden von OnDeleting und OnDeleted  
 Sie können `OnDeleting()` oder `OnDeleted()` in einer Domänenklasse oder in einer Domänenbeziehung überschreiben.  
  
1.  <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A> wird aufgerufen, wenn ein Element im Begriff ist gelöscht zu werden, aber bevor seine Beziehungen getrennt wurden. Die Navigation zwischen dem Element und anderen Elementen ist noch möglich, und es befindet sich noch in `store.ElementDirectory`.  
  
     Wenn mehrere Elemente gleichzeitig gelöscht werden, wird OnDeleting für alle aufgerufen, bevor die Löschungen ausgeführt werden.  
  
     `IsDeleting` hat den Wert "True".  
  
2.  <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A> wird aufgerufen, nachdem das Element gelöscht wurde. Es verbleibt im CLR-Heap, sodass ggf. ein "Undo" ausgeführt werden kann, aber es ist nicht mehr mit anderen Elementen verbunden und wurde aus `store.ElementDirectory` entfernt. Für Beziehungen verweisen die Rollen immer noch die alte Rolleninhaber.`IsDeleted` ist "true".  
  
3.  "OnDeleting" und "OnDeleted" werden aufgerufen, wenn der Benutzer nach dem Erstellen eines Elements "Undo" aufruft und wenn eine frühere Löschung in "Redo" wiederholt wird. Verwenden Sie `this.Store.InUndoRedoOrRollback`, um die Aktualisierung von Speicherelementen in diesen Fällen zu vermeiden. Weitere Informationen finden Sie unter [wie: Verwenden von Transaktionen zum Aktualisieren des Modells](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
 Im folgenden Code wird z. B. ein Album gelöscht, wenn der letzte untergeordnete Song des Albums gelöscht wird:  
  
```  
  
// Delete the parent Album when the last Song is deleted.  
// Override methods in the embedding relationship between Album and Song:  
partial class AlbumHasSongs  
{  
  protected override void OnDeleted()  
  {  
    base.OnDeleted();  
    // Don't perform in-store actions in undo:  
    if (this.Store.InUndoRedoOrRollback) return;  
    // Relationship source and target still work:  
    // Don't bother if source is already on its way out:  
    if (!this.Album.IsDeleting && !this.Album.IsDeleted)  
    {  
      if (this.Album.Songs.Count == 0)  
      {   
        this.Album.Delete();  
} } } }  
  
```  
  
 Häufig ist es sinnvoller, die Löschung durch die Löschung der Beziehung statt des Rollenelements auszulösen, da dies sowohl beim Löschen des Elements als auch beim Löschen der Beziehung selbst funktioniert. Aber bei einer Verweisbeziehung möchten Sie die Löschung vielleicht weitergeben, wenn ein verwandtes Element gelöscht wird und nicht wenn die Beziehung selbst gelöscht wird. In diesem Beispiel wird ein Album gelöscht, wenn der letzte mitwirkende Interpret gelöscht wird. Es erfolgt jedoch keine Reaktion, wenn die Beziehungen gelöscht werden:  
  
```  
using System.Linq; ...  
// Assumes a many-many reference relationship   
// between Artist and Album.    
partial class Artist  
{  
  protected override void OnDeleting()  
  {  
    base.OnDeleting();  
    if (this.Store.InUndoRedoOrRollback) return;  
    List<Album> toDelete = new List<Album>();  
    foreach (Album album in this.Albums)  
    {  
      if (album.Artists.Where(artist => !artist.IsDeleting)  
                        .Count() == 0)  
      {  
        toDelete.Add(album);  
      }  
    }  
    foreach (Album album in toDelete)  
    {  
      album.Delete();  
} } }  
  
```  
  
 Wenn Sie für ein Element <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A> ausführen, werden "OnDeleting" und "OnDeleted" aufgerufen. Diese Methoden werden ausgeführte Inline - immer, also unmittelbar vor und nach dem tatsächlichen löschen. Wenn im Code mindestens zwei Elemente gelöscht werden, werden "OnDeleting" und "OnDeleted" abwechselnd für alle Elemente aufgerufen.  
  
##  <a name="rules"></a> Von Löschregeln und Ereignisse  
 Als Alternative zu OnDelete-Handlern können Sie Löschregeln und Löschereignisse definieren.  
  
1.  **Löschen von** und **löschen** Regeln ausgelöst werden, nur in einer Transaktion und nicht in einem zum Rückgängigmachen oder wiederherstellen. Sie können festlegen, dass sie in die Warteschlange gestellt und am Ende der Transaktion ausgeführt werden, in der die Löschung erfolgt. "Deleting"-Regeln werden immer vor "Deleted"-Regeln ausgeführt, die sich in der Warteschlange befinden.  
  
     Verwenden Sie Regeln, um Änderungen weiterzugeben, die nur Elemente im Speicher betreffen, wie Beziehungen, Diagrammelemente und deren Eigenschaften. Normalerweise wird eine "Deleting"-Regel zur Weitergabe der Löschung verwendet und eine "Delete"-Regel zum Erstellen von Ersetzungselementen und -beziehungen.  
  
     Weitere Informationen finden Sie unter [weitergeben Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).  
  
2.  **Gelöschte** Store-Ereignis wird am Ende einer Transaktion aufgerufen und wird aufgerufen, nachdem ein Rückgängigmachen oder wiederholen. Es kann daher verwendet werden, um Löschungen von Objekten außerhalb des Speichers weiterzugeben, wie Dateien, Datenbankeinträge oder andere Objekte in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Weitere Informationen finden Sie unter [Handler verteilt Änderungen außerhalb der Ereignismodell](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
    > [!WARNING]
    >  Nachdem ein Element gelöscht wurde, können Sie noch auf die Werte seiner Domäneneigenschaften zugreifen, aber nicht mehr durch Beziehungslinks navigieren. Legen Sie dagegen ein Deleted-Ereignis für eine Beziehung fest, können Sie auch auf die beiden Elemente zugreifen, die die Rollen der Beziehung innehatten. Aus diesem Grund Wenn möchten Antworten auf die Löschung eines Modellelements, jedoch soll auf ein Element zuzugreifen, mit denen sie verknüpft wurde, legen Sie einen Delete-Ereignis für die Beziehung anstelle von dem Modellelement Domänenklasse.  
  
### <a name="example-deletion-rules"></a>Beispiele für Löschregeln  
  
```  
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]  
internal class AlbumDeletingRule : DeletingRule  
{  
  public override void ElementDeleting(ElementDeletingEventArgs e)  
  {  
    base.ElementDeleting(e);  
    // ...perform tasks to propagate imminent deletion  
  }  
}  
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]  
internal class AlbumDeletedRule : DeleteRule  
{  
  public override void ElementDeleted(ElementDeletedEventArgs e)  
  {  
    base.ElementDeleted(e);  
    // ...perform tasks such as creating new elements  
  }  
}  
  
// The rule must be registered:  
public partial class MusicLibDomainModel  
{  
  protected override Type[] GetCustomDomainModelTypes()  
  {  
    List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
    types.Add(typeof(AlbumDeletingRule));  
    types.Add(typeof(AlbumDeletedRule));  
    // If you add more rules, list them here.   
    return types.ToArray();  
  }  
}  
  
```  
  
### <a name="example-deleted-event"></a>Beispiel für ein Deleted-Ereignis  
  
```  
partial class NestedShapesSampleDocData  
{  
  protected override void OnDocumentLoaded(EventArgs e)  
  {  
    base.OnDocumentLoaded(e);  
    DomainRelationshipInfo commentRelationship =   
          this.Store.DomainDataDirectory  
          .FindDomainRelationship(typeof(CommentsReferenceComponents));  
  
    this.Store.EventManagerDirectory.ElementDeleted.Add(commentRelationship,  
      new EventHandler<ElementDeletedEventArgs>(CommentLinkDeleted));  
  }  
  
  private void CommentLinkDeleted (object sender, ElementDeletedEventArgs e)  
  {  
    CommentsReferenceComponents link = e.ModelElement as CommentsReferenceComponents;  
    Comment comment = link.Comment;  
    Component component = link.Subject;  
    if (comment.IsDeleted)  
    {  
      // The link was deleted because the comment was deleted.  
      System.Windows.Forms.MessageBox.Show("Removed comment on " + component.Name);  
    }  
    else  
    {  
      // It was just the link that was deleted - the comment itself remains.  
      System.Windows.Forms.MessageBox.Show("Removed comment link to "   
           + component.Name);  
    }  
  }  
}  
  
```  
  
##  <a name="unmerge"></a> Verbund aufheben  
 Der Vorgang, der ein untergeordnetes Element zum übergeordneten fügt heißt *Merge*. Er tritt auf, wenn ein neues Element oder eine neue Gruppe von Elementen über den Werkzeugkasten erstellt, aus einem anderen Teil des Modells verschoben oder aus der Zwischenablage kopiert wird. Neben dem Erstellen einer einbettenden Beziehung zwischen dem übergeordneten und dem neuen untergeordneten Element können beim Zusammenführungsvorgang weitere Beziehungen eingerichtet, Hilfselemente erstellt und Eigenschaftenwerte in den Elementen festgelegt werden. Der Zusammenführungsvorgang ist in eine Elementzusammenführungsdirektive (Element Merge Directive, EMD) eingebettet.  
  
 Ein EMD kapselt auch des komplementären Cmdlets *Verbund aufheben* oder `MergeDisconnect` Vorgang. Soll aus einem durch Zusammenführung erstellten Cluster ein Element entfernt werden, wird empfohlen den zugehörigen Vorgang zum Aufheben der Zusammenführung zu verwenden, wenn die verbleibenden Elemente in einem konsistenten Zustand hinterlassen werden sollen. Beim Vorgang zum Aufheben der Zusammenführung werden üblicherweise die Techniken verwendet, die in den vorherigen Abschnitten beschrieben wurden.  
  
 Weitere Informationen finden Sie unter [Element erstellen anpassen und Bewegung](../modeling/customizing-element-creation-and-movement.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md)   
 [Anpassen von Element erstellen und verschieben](../modeling/customizing-element-creation-and-movement.md)   
 [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)