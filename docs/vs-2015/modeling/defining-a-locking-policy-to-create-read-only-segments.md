---
title: Definieren einer Sperrrichtlinie zum Erstellen von schreibgeschützten Segmenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 298e649704731157164db363dfa198ff6f2cdc41
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893824"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definieren einer Sperrrichtlinie zum Erstellen von schreibgeschützten Segmenten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Unveränderlichkeit-API, der die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualisierungs- und Modellierungs-SDK können Sie ein Programm, um die Sperre Teils oder aller ein Modell einer domänenspezifischen Sprache (DSL), damit sie zwar gelesen, aber nicht geändert. Diese schreibgeschützte Option kann verwendet werden, z. B., damit ein Benutzer lassen Kollegen mit Anmerkungen versehen, und überprüfen eine DSL-Modell, jedoch kann verhindern, dass sie die ursprüngliche ändern.  
  
 Sie können darüber hinaus als Autor einer DSL und definieren eine *Sperrrichtlinie.* Eine Sperrrichtlinie definiert, welche Sperren zulässigen, nicht zulässig oder erforderlich sind. Wenn Sie eine DSL veröffentlichen, können Sie z. B. Drittanbieter-Entwickler so erweitern, mit neuen Befehlen empfehlen. Aber Sie können auch eine Sperrrichtlinie verwenden, um zu verhindern, dass Sie den schreibgeschützten Status des angegebenen Teile des Modells ändern.  
  
> [!NOTE]
>  Eine Sperrrichtlinie kann umgangen werden, mithilfe der Reflektion. Stellt eine klare Hürde für externe Entwickler, sondern bietet keine hohe Sicherheit.  
  
 Weitere Informationen und Beispiele finden Sie unter den [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [Visualisierungs- und Modellierungs-SDK](http://go.microsoft.com/fwlink/?LinkId=186128) Website.  
  
## <a name="setting-and-getting-locks"></a>Festlegen und Abrufen von Sperren  
 Sie können das Sperren auf den Speicher, auf einer Partition oder auf ein einzelnes Element festlegen. Beispielsweise diese Anweisung wird verhindert, dass ein Modellelement gelöscht wird, und verhindert auch die Eigenschaften geändert wird:  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 Andere Werte für die Sperre können verwendet werden, um Änderungen in Beziehungen, elementerstellung, datenverschiebung zwischen Partitionen und neu sortieren Links in einer Rolle zu verhindern.  
  
 Die Sperren gelten Benutzeraktionen und Programmcode. Wenn Sie Programmcode versucht, eine Änderung einer `InvalidOperationException` ausgelöst. Sperren werden in einen Rückgängig- oder Wiederholen-Vorgang ignoriert.  
  
 Sie können ermitteln, ob ein Element in einer angegebenen Menge mit jeder gesperrt hat `IsLocked(Locks)` und Sie erhalten den aktuellen Satz von Sperren auf ein Element mit `GetLocks()`.  
  
 Sie können eine Sperre festlegen, ohne Verwendung einer Transaktions. Die Lock-Datenbank ist nicht Teil des Speichers. Wenn Sie eine Sperre in Reaktion auf eine Änderung eines Werts in den Speicher festlegen, sollten z. B. in "OnValueChanged", Sie Änderungen ermöglichen, die Teil eines Rückgängig-Vorgangs sind.  
  
 Diese Methoden sind Erweiterungsmethoden bereit, die definiert sind, die die <xref:Microsoft.VisualStudio.Modeling.Immutability> Namespace.  
  
### <a name="locks-on-partitions-and-stores"></a>Sperren für Partitionen und Speicher  
 Sperren können auch Partitionen und den Speicher angewendet werden. Eine Sperre, die auf einer Partition festgelegt ist, gilt für alle Elemente in der Partition. Aus diesem Grund wird z. B. die folgende Anweisung alle Elemente in einer Partition verhindert gelöscht wird, unabhängig von der die Zustände von ihren eigenen Sperren erzeugt wurde. Sonstiger Sperren dennoch, wie z. B. `Locks.Property` konnte weiterhin für einzelne Elemente festgelegt werden:  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 Eine Sperre, die für den Store festgelegt wird, gilt für alle Elemente, unabhängig von den Einstellungen der diese Sperre für die Partitionen und die Elemente.  
  
### <a name="using-locks"></a>Verwenden von Sperren  
 Sie können Sperren verwenden, um Schemas, z. B. den folgenden Beispielen zu implementieren:  
  
-   Unterbinden Sie Änderungen an allen Elementen und Beziehungen mit Ausnahme derjenigen, die Kommentare darstellen. Dadurch können Benutzer ein Modell mit Anmerkungen versehen, ohne ihn zu ändern.  
  
-   Änderungen in der Standardpartition nicht zulassen, aber Änderungen in der Partition Diagramm zulassen. Die Benutzer kann das Diagramm ändern, aber das zugrunde liegende Modell kann nicht geändert werden.  
  
-   Unterbinden Sie Änderungen an den Store mit Ausnahme von einer Gruppe von Benutzern, die in einer separaten Datenbank registriert sind. Für andere Benutzer sind das Diagramm und das Modell schreibgeschützt.  
  
-   Änderungen für das Modell nicht zulassen, wenn eine boolesche Eigenschaft des Diagramms festgelegt ist auf "true". Geben Sie einen Menübefehl, diese Eigenschaft zu ändern. Dadurch wird sichergestellt, Benutzer, die sie keine versehentlich ändert.  
  
-   Nicht zulassen Sie, hinzufügen und Löschen von Elementen und Beziehungen zwischen bestimmten Klassen, doch gestatten Sie eigenschaftenänderungen. Dies bietet Benutzern mit einem festen Formular, in dem sie die Eigenschaften gefüllt werden können.  
  
## <a name="lock-values"></a>Lock-Werte  
 Sperren können für eine Store, Partitions- oder einzelne ModelElement festgelegt werden. Sperrt eine `Flags` Enumeration: können kombiniert werden die Werte, die mit "&#124;".  
  
- Sperren ein ModelElement enthalten immer die Sperren der Partition.  
  
- Sperren einer Partition enthalten immer den Sperren der Store.  
  
  Sie können keine Sperre für eine Partition festlegen oder speichern, und deaktivieren zur gleichen Zeit die Sperre für ein einzelnes Element.  
  
|Wert|D. h., wenn `IsLocked(Value)` ist "true"|  
|-----------|------------------------------------------|  
|Keiner|Keine Einschränkung.|  
|Eigenschaft|Domäneneigenschaften der Elemente werden nicht geändert. Dies gilt nicht für Eigenschaften, die von der Rolle einer Domänenklasse in einer Beziehung generiert werden.|  
|Hinzufügen|Neue Elemente und Links kann nicht in einer Partition erstellt werden oder zu speichern.<br /><br /> Gilt nicht für `ModelElement`.|  
|Verschieben|Element kann nicht zwischen Partitionen verschoben werden, wenn `element.IsLocked(Move)` ist "true", oder wenn `targetPartition.IsLocked(Move)` ist "true".|  
|Löschen|Ein Element kann nicht gelöscht werden, wenn diese Sperre, bei dem Element selbst festgelegt wird oder auf einem der Elemente, die die Löschung weitergegeben werden, z. B. eingebettete Elemente und Formen sollen würde.<br /><br /> Sie können `element.CanDelete()` zu ermitteln, ob ein Element gelöscht werden kann.|  
|Neu anordnen|Die Reihenfolge von Links zu einer das Roleplayer kann nicht geändert werden.|  
|RolePlayer|Die Gruppe der Links, die an diesem Element als Quelle haben, kann nicht geändert werden. Neue Elemente können z. B. können nicht unter diesem Element eingebettet werden. Diese wirkt Links sich nicht für die dieses Element auf das Ziel ist.<br /><br /> Wenn dieses Element über einen Link ist, sind die Quelle und Ziel nicht betroffen.|  
|Alle|Bitweise OR der anderen Werte.|  
  
## <a name="locking-policies"></a>Richtlinien für Sperren  
 Als Autor einer DSL, können Sie definieren eine *Sperrrichtlinie*. Eine Sperrrichtlinie regelt den Betrieb des SetLocks(), damit Sie bestimmte Sperren verhindern können, wird festgelegt, oder festlegen, dass bestimmte Sperren festgelegt werden müssen. In der Regel würden Sie eine Sperrrichtlinie verwenden, um Sie davon abhalten, Benutzer oder Entwickler von begehen versehentlich die beabsichtigte Verwendung einer DSL, auf die gleiche Weise, dass Sie eine Variable deklarieren können `private`.  
  
 Sie können auch eine Sperrrichtlinie verwenden, um Sperren für alle Elemente abhängig von der Typ des Elements festgelegt. Grund hierfür ist, `SetLocks(Locks.None)` wird immer aufgerufen, wenn ein Element erstellt wird oder aus der Datei deserialisiert.  
  
 Allerdings können nicht Sie eine Richtlinie verwenden, um die Sperren für ein Element während seiner Lebensdauer zu variieren. Um diesen Effekt zu erzielen, verwenden Sie Aufrufe von `SetLocks()`.  
  
 Zum Definieren einer Sperrrichtlinie müssen Sie:  
  
-   Erstellen Sie eine Klasse, die das <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> implementiert.  
  
-   Fügen Sie dieser Klasse mit den Diensten, die über das docdata-Objekt Ihrer DSL zur Verfügung stehen.  
  
### <a name="to-define-a-locking-policy"></a>Zum Definieren einer Sperrrichtlinie  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> weist folgende Definition:  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 Diese Methoden werden aufgerufen, wenn ein Aufruf an erfolgt `SetLocks()` in einem Store, Partitions- oder ModelElement. In jeder Methode erhalten Sie mit einem vorgeschlagenen Satz von Sperren. Sie können den vorgeschlagenen Satz zurückgeben, oder Sie können von Addition und Subtraktion von Sperren.  
  
 Zum Beispiel:  
  
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
  
 Um sicherzustellen, dass Benutzer immer löschen können Codeelemente, auch wenn andere Aufrufe `SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 Die Änderung in alle Eigenschaften jedes Elements von MyClass zu unterbinden:  
  
 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`  
  
### <a name="to-make-your-policy-available-as-a-service"></a>Um die Richtlinie als Dienst verfügbar zu machen  
 In Ihrer `DslPackage` fügen eine neue Datei, die Code enthält, die im folgende Beispiel ähnelt:  
  
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



