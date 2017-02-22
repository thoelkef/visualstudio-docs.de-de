---
title: "Definieren einer Sperrrichtlinie zum Erstellen von schreibgesch&#252;tzten Segmenten | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 12
caps.handback.revision: 12
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Definieren einer Sperrrichtlinie zum Erstellen von schreibgesch&#252;tzten Segmenten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Unveränderlichkeit API des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualisierung und Modellieren SDK bietet dem Sperren beteiligt ein Programm oder die ganze domänenspezifisches Modell der Sprache \(DSL\), sodass sie gelesen, jedoch nicht geändert werden kann.  Diese schreibgeschützte Option kann verwendet werden, damit ein Benutzer beispielsweise fordern Kollegen überprüfen und auskommentieren kann, kann ein DSL\-Modell aber sie aus dem Ändern der Vorlage nicht zulässig.  
  
 Außerdem als Autor eines DSL, können Sie die *Richtlinie Sperren*definieren *.* Eine Richtlinie Sperren definiert sind zulässig, die keine Sperren zugelassen oder erforderlich.  Wenn Sie beispielsweise ein DSL veröffentlichen, können Sie die Entwickler von Drittanbietern anregen, mit neuen Befehle zu erweitern.  Aber Sie können eine Richtlinie für Sperren verwendet werden, um zu verhindern, dass sie den Schreibschutzstatus der angegebenen Teile des Modells ändern.  
  
> [!NOTE]
>  Eine Richtlinie Sperren kann umgangen werden, indem die Reflektion verwendet.  Es stellt eine übersichtliche Grenzwert für Entwickler von Drittanbietern bereit, bietet jedoch nicht werthaltige Sicherheit.  
  
 Weitere Informationen und Beispiele sind in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)][Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkId=186128) Website verfügbar.  
  
## Das Festlegen und Abrufen Sperren  
 Sie können festlegen sperren den Speicher für eine Partition oder auf ein einzelnes Element.  Diese Anweisung wird beispielsweise ein Modellelement gelöscht wird und verhindert auch auf ihre Eigenschaften geändert werden:  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 Andere Werte für Sperren verwendet werden können, um Änderungen in den Beziehungen Elementerstellung, zeigen Sie mit dem zwischen Partitionen zu verhindern und Neuanordnen von Links in einer Rolle.  
  
 Sperren gelten auf Benutzeraktionen und Programmcode.  Wenn Programmcode versucht, eine Änderung vorzunehmen, wird `InvalidOperationException` ausgelöst.  Sperren werden ignoriert in einem Rückgängig\- oder einem Wiederholungsvorgang.  
  
 Sie können ermitteln, ob ein Element eine beliebige Sperre in einem bestimmten Satz wurde, indem Sie `IsLocked(Locks)` verwenden, und Sie erhalten können, der den aktuellen Satz von Sperren auf einem Element, indem Sie `GetLocks()`verwenden.  
  
 Sie können eine Sperre festzulegen, ohne eine Transaktion zu verwenden.  Die Sperren Zieldatenbank ist nicht Teil des Speichers.  Beim Festlegen einer Sperre als Reaktion auf eine Änderung eines Werts im Speicher, z. B. in OnValueChanged Änderungen zu ermöglichen, die Teil eines Rückgängig\-Vorgangs sind.  
  
 Diese Methoden sind Erweiterungsmethoden, die im <xref:Microsoft.VisualStudio.Modeling.Immutability>\-Namespace definiert sind.  
  
### Sperrt ein und speichert Partitionen  
 Sperrt kann in den Partitionen und im Speicher ebenfalls angewendet werden.  Eine Sperre, die für eine Partition festgelegt ist, gilt für alle Elemente in der Partition.  Daher verhindert beispielsweise die folgende Anweisung alle Elemente in einer Partition gelöscht wird, ungeachtet der Zustände aus ihrem eigenen Sperren.  Trotzdem kann `Locks.Property` wie andere Sperren für einzelne Elemente noch festgelegt werden:  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 Eine Sperre, die im Speicher festgelegt ist, gilt für alle Elemente, ungeachtet der Einstellungen dieser Sperre der Partitionen und Elementen zu.  
  
### Verwenden von Sperren  
 Verwenden Sie könnten z. B. Schemas sperren, um die folgenden Beispiele zu implementieren:  
  
-   Zulassen von Änderungen nicht an allen Elementen und Beziehungen, mit Ausnahme der die Kommentare darstellen.  Dies ermöglicht es Benutzern, um ein Modell zu gestalten, ohne es zu ändern.  
  
-   Zulassen von Änderungen nicht in der Standardpartition, jedoch können Sie Änderungen im Diagramm partition.  Der Benutzer kann das Diagramm neu anordnen, kann aber das zugrunde liegende Modell nicht ändern.  
  
-   Zulassen von Änderungen im Speicher nicht mit Ausnahme einer Benutzergruppe, die in einer separaten Datenbank registriert sind.  Für andere Benutzer sind das Diagramm und das Modell schreibgeschützt.  
  
-   Zulassen von Änderungen am Modell nicht, wenn eine boolesche Eigenschaft des Diagramms auf true festgelegt ist.  Erstellen Sie einen Menübefehl bereit, diese Eigenschaft zu ändern.  Dadurch wird verhindert, dass Benutzer Änderungen, die sie nicht versehentlich ausführen.  
  
-   Zulassen nicht Sie Hinzufügen und Löschen von Elementen und Beziehungen bestimmter Klassen, jedoch können Sie Änderungen an den Eigenschaften.  Dies bietet Benutzern mit einem festen Formular, das sie die Eigenschaften gefüllt werden können.  
  
## Sperren von Werten  
 Sperrt kann in einem Speicher, einer Partition oder einer Person ModelElement festgelegt werden.  Sperrt ist eine `Flags`\-Enumeration: Sie können mithilfe seiner Werte kombinieren „&#124;“.  
  
-   Sperren von einem ModelElement Einschließen von der Partition stets sperrt.  
  
-   Zu einem von Sperren sperrt immer die Partition aus dem Speicher.  
  
 Sie können eine Sperre für eine Partition oder einem Speicher nicht festlegen und gleichzeitig die Sperre für ein einzelnes Element deaktivieren.  
  
|Wert|true, wenn `IsLocked(Value)` Bedeutung|  
|----------|--------------------------------------------|  
|None|Keine Einschränkungen.|  
|Property|Domäneneigenschaften von Elementen können nicht geändert werden.  Dies gilt nicht für Eigenschaften zu, die von der Rolle eine Domänenklasse in einer Beziehung generiert werden.|  
|add|Neue Elemente und Links können nicht in einer Partition oder in einem Speicher erstellt werden.<br /><br /> Nicht zutreffend `ModelElement`soll.|  
|Verschieben|Das Element kann nicht zwischen Partitionen verschoben werden, wenn `element.IsLocked(Move)` auf true festgelegt ist oder wenn `targetPartition.IsLocked(Move)` true ist.|  
|Delete|Ein Element kann nicht, wenn diese Sperre für das Element selbst festgelegt oder auf einem der Elemente, mit denen Löschen weitergeben, z. B. eingebettete Elemente und Formen gelöscht werden.<br /><br /> Sie können `element.CanDelete()` verwenden, um zu ermitteln, ob ein Element gelöscht werden kann.|  
|Neu anordnen|Die Reihenfolge von Links zu einem roleplayer kann nicht geändert werden.|  
|RolePlayer|Der Satz von Links, die an dieses Element Ursprungs sind, kann nicht geändert werden.  Zum Beispiel können neue Elemente nicht in diesem Element enthalten sind.  Dies wirkt sich nicht auf Links, für die dieses Element als Ziel hat.<br /><br /> Wenn dieses Element ein Link ist, sind ihre Quelle und Ziel nicht betroffen.|  
|Alle|Bitweises OR den anderen Werten.|  
  
## Sperren\-politische Richtlinien  
 Als Autor eines DSL, können Sie die *Richtlinie Sperren*definieren.  Eine Richtlinie Sperren von SetLocks\(\) moderiert den Vorgang, sodass Sie können verhindern, dass ein bestimmtes von Sperren gesetzt werden oder bestimmt, dass weist Sperren festgelegt werden muss.  Normalerweise würden Sie eine Richtlinie Sperren verwenden, um Benutzern oder Entwickler von dem zuwiderhandeln die Verwendung eines DSL versehentlich zu entmutigen auf die gleiche Weise `private`, wenn Sie die Variable deklarieren können.  
  
 Sie können eine Richtlinie Sperren auch verwenden, um festzulegen, die Sperren für alle Elemente vom Typ des Elements abhängig sind.  Dies liegt daran, dass `SetLocks(Locks.None)` immer aufgerufen wird, wenn ein Element zum ersten Mal der Datei erstellt oder deserialisiert wird.  
  
 Sie können jedoch eine Richtlinie nicht verwenden, um Sperren zu unterscheiden sich bei einem Element während seiner Lebensdauer.  Um diesen Effekt zu erzielen, sollten Sie Aufrufe `SetLocks()`verwenden.  
  
 So erstellen Sie eine Richtlinie Sperren definieren, müssen Sie Folgendes:  
  
-   Erstellen Sie eine Klasse, die <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>implementiert.  
  
-   Fügen Sie dieser Klasse den Diensten hinzugefügt, die vom DocData des DSL verfügbar sind.  
  
### So definieren Sie eine Richtlinie Sperren  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> weist folgende Definition auf:  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 Diese Methoden werden aufgerufen, wenn `SetLocks()` ein Aufruf für einen Speicher, einer Partition oder zu einem ModelElement gemacht wird.  In jeder Methode wird ein Satz von Vorgeschlagen Sperren zu gewährleisten.  Sie können den vorgeschlagenen Satz zurückgeben, oder Sie können hinzufügen und zu subtrahierende Sperren.  
  
 Beispiele:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{  
  public class MyLockingPolicy : ILockingPolicy  
  {  
    /// <summary>  
    /// Moderate SetLocks(this ModelElement target, Locks locks)  
    /// </summary>  
    /// <param name="element">target</param>  
    /// <param name="proposedLocks">locks</param>  
    /// <returns></returns>  
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)  
    {  
      // In my policy, users can never delete an element,  
      // and other developers cannot easily change that:  
      return proposedLocks | Locks.Delete);  
    }  
    public Locks RefineLocks(Store store, Locks proposedLocks)  
    {  
      // Only one user can change this model:  
      return Environment.UserName == "aUser"   
           ? proposedLocks : Locks.All;  
    }  
  
```  
  
 So überprüfen Sie, ob Benutzer Elemente immer löschen können, selbst wenn `SetLocks(Lock.Delete):`anderer Code aufruft  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 Um Änderungen in allen Eigenschaften jedes Elements von MyClass nicht zulässig:  
  
 `return element is MyClass ?  (proposedLocks | Locks.Property) : proposedLocks;`  
  
### Um die Richtlinien bereitstellen als Dienst  
 Fügen Sie im `DslPackage` Projekt eine neue Datei hinzufügen, die Code enthält, der dem folgenden Beispiel ähnelt:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{   
  // Override the DocData GetService() for this DSL.  
  internal partial class YourDslDocData // Change  
  {  
    /// <summary>  
    /// Custom locking policy cache.  
    /// </summary>  
    private ILockingPolicy myLockingPolicy = null;  
  
    /// <summary>  
    /// Called when a service is requested.  
    /// </summary>  
    /// <param name="serviceType">Service requested</param>  
    /// <returns>Service implementation</returns>  
    public override object GetService(System.Type serviceType)  
    {  
      if (serviceType == typeof(SLockingPolicy)   
       || serviceType == typeof(ILockingPolicy))  
      {  
        if (myLockingPolicy == null)  
        {  
          myLockingPolicy = new MyLockingPolicy();  
        }  
        return myLockingPolicy;  
      }  
      // Request is for some other service.  
      return base.GetService(serviceType);  
    }  
}  
```