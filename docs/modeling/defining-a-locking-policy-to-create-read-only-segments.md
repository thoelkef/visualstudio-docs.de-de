---
title: Definieren einer Richtlinie sperren, um nur-Lese Segmente erstellen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: "12"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 0ac8ba75920c4b3b8964d473258c162c256139ca
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definieren einer Sperrrichtlinie zum Erstellen von schreibgeschützten Segmenten
Die Unveränderlichkeit-API, der die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK ermöglicht ein Programm, um die Sperre Teils oder aller eine domänenspezifische Sprache (DSL)-Modell, damit sie gelesen aber nicht geändert werden kann. Diese schreibgeschützte Option kann verwendet werden, z. B., damit ein Benutzer kann Kollegen dazu ein, mit einer Anmerkung versehen, und überprüfen einen DSL-Modell bitten, jedoch kann verhindern, dass sie die ursprüngliche ändern.  
  
 Sie können darüber hinaus als Autor einer DSL definieren eine *Sperrrichtlinie.* Eine Sperre Richtlinie definiert, welche Sperren zulässigen, nicht zulässig oder erforderlich sind. Wenn Sie eine DSL veröffentlichen, können z. B. Drittanbieter-Entwickler mit neuen Befehle zu erweitern fördern. Aber Sie können eine Sperrungsrichtlinie auch verwenden, um zu verhindern, dass sie den schreibgeschützten Status der angegebenen Teile des Modells ändern.  
  
> [!NOTE]
>  Eine Richtlinie Sperre kann umgangen werden, mithilfe der Reflektion. Stellt eine klare Hürde für Entwickler von Drittanbietern, aber bietet keine hohe Sicherheit.  
  
 Weitere Informationen und Beispiele finden Sie unter der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkId=186128) Website.  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
## <a name="setting-and-getting-locks"></a>Festlegen und Abrufen von Sperren  
 Sie können die Sperren für den Speicher, auf eine Partition oder auf einem einzelnen Element festlegen. Beispielsweise wird diese Anweisung wird verhindert, dass ein Modellelement gelöscht wird und auch verhindert, dessen Eigenschaften geändert wird:  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 Andere Werte für die Sperre können verwendet werden, um Änderungen in Beziehungen, Element erstellen, Verschieben von Partitionen und neu anordnen Links in einer Rolle zu verhindern.  
  
 Die Sperren gelten sowohl auf Benutzeraktionen und Programmcode. Wenn Sie Programmcode versucht, eine Änderung vorzunehmen, einen `InvalidOperationException` ausgelöst. Sperren werden in einem Vorgang zum Rückgängigmachen oder Wiederholen ignoriert.  
  
 Sie können ermitteln, ob ein Element alle in einem angegebenen Satz mit sperrt `IsLocked(Locks)` und Sie können mit den aktuellen Satz von Sperren für ein Element abrufen `GetLocks()`.  
  
 Sie können eine Sperre festlegen, ohne Verwendung einer Transaktions. Die Lock-Datenbank ist nicht Teil des Store. Wenn Sie eine Sperre in Reaktion auf eine Änderung eines Werts im Speicher festlegen, sollte z. B. OnValueChanged, Sie Änderungen ermöglichen, die Teil eines Rückgängig-Vorgangs sind.  
  
 Diese Methoden Erweiterungsmethoden, sind, die in definiert werden die <xref:Microsoft.VisualStudio.Modeling.Immutability> Namespace.  
  
### <a name="locks-on-partitions-and-stores"></a>Sperren für Partitionen und-Speicher  
 Sperren können auch Partitionen und den Speicher angewendet werden. Eine Sperre, die für eine Partition festgelegt wird, gilt für alle Elemente in der Partition. Aus diesem Grund kann z. B. die folgende Anweisung alle Elemente in einer Partition nicht gelöscht werden, unabhängig von den Status der eigene Sperren. Andere Sperren trotzdem, z. B. `Locks.Property` weiterhin für einzelne Elemente festgelegt werden:  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 Eine Sperre, die für den Speicher festlegt wird gilt für alle Elemente, unabhängig von den Einstellungen dieser Sperre für die Partitionen und die Elemente.  
  
### <a name="using-locks"></a>Verwendung von Sperren  
 Sperren können Sie um Schemas, z. B. die folgenden Beispiele zu implementieren:  
  
-   Unterbinden Sie Änderungen an alle Elemente und Beziehungen mit Ausnahme derjenigen, die Kommentare darstellen. Dadurch können Benutzer ein Modell mit Anmerkungen versehen, ohne es zu ändern.  
  
-   Unterbinden Sie Änderungen in die Standardpartition, aber lassen Sie die Änderungen in der Partition Diagramm. Der Benutzer kann das Diagramm ändern, aber das zugrunde liegende Modell kann nicht geändert werden.  
  
-   Unterbinden Sie Änderungen an den Speicher mit Ausnahme von einer Gruppe von Benutzern an, die in einer separaten Datenbank registriert sind. Sind für andere Benutzer schreibgeschützt sind und das Diagramm und Modell.  
  
-   Änderungen am Modell zu unterbinden, wenn eine boolesche Eigenschaft des Diagramms festgelegt ist auf "true". Geben Sie einen Menübefehl, um diese Eigenschaft zu ändern. Dadurch wird sichergestellt, Benutzer, die sie nicht vornehmen versehentlich geändert werden.  
  
-   Zu unterbinden Sie, hinzufügen und Löschen von Elementen und Beziehungen zwischen bestimmten Klassen, doch gestatten Sie Eigenschaft ändert. Dies bietet Benutzern eine feste Form, in der die Eigenschaften aufgefüllt werden können.  
  
## <a name="lock-values"></a>Lock-Werte  
 Sperren können für eine Store, Partitions- oder einzelne Modellelement festgelegt werden. Sperren einer `Flags` Enumeration: können Sie dessen Werte mit kombinieren "&#124;".  
  
-   Sperren von einem Modellelement enthalten immer die Sperren der Partition an.  
  
-   Sperren einer Partition enthalten immer die Sperren des Speichers.  
  
 Sie können keine Sperre für eine Partition festlegen oder speichern und zur gleichen Zeit deaktivieren die Sperre für ein einzelnes Element.  
  
|Wert|D. h. wenn `IsLocked(Value)` ist "true"|  
|-----------|------------------------------------------|  
|Keine|Keine Einschränkung.|  
|Eigenschaft|Domäneneigenschaften Elemente können nicht geändert werden. Dies gilt nicht für Eigenschaften, die von der Rolle einer Domäne-Klasse in einer Beziehung generiert werden.|  
|Hinzufügen|Neue Elemente und Verknüpfungen können in einer Partition können nicht erstellt werden oder gespeichert.<br /><br /> Gilt nicht für `ModelElement`.|  
|Verschieben|Element kann nicht zwischen Partitionen verschoben werden, wenn `element.IsLocked(Move)` ist "true", oder wenn `targetPartition.IsLocked(Move)` ist "true".|  
|Löschen|Ein Element kann nicht gelöscht werden, wenn diese Sperre für das Element selbst festgelegt ist, oder auf eines der Elemente auf die Löschung weitergegeben werden, z. B. eingebettete Elemente und Formen sollen würde.<br /><br /> Sie können `element.CanDelete()` ermitteln Sie, ob ein Element gelöscht werden kann.|  
|Neu anordnen|Die Reihenfolge der Links bei einem das Roleplayer kann nicht geändert werden.|  
|Das RolePlayer|Die Gruppe der Links, die auf dieses Element belegen kann nicht geändert werden. Beispielsweise können nicht die neue Elemente unter diesem Element eingebettet werden. Dies hat keine Auswirkungen, Links für die dieses Element das Ziel ist.<br /><br /> Wenn dieses Element über einen Link handelt, sind seine Quelle und Ziel nicht betroffen.|  
|Alle|Bitweise OR der anderen Werte.|  
  
## <a name="locking-policies"></a>Sperren von Richtlinien  
 Sie können als Autor von DSL, definieren eine *Sperrrichtlinie*. Eine Sperrungsrichtlinie teilweise den Betrieb der SetLocks(), sodass Sie spezifischen Sperren verhindern können, festgelegt oder festlegen, dass bestimmte Sperren festgelegt werden müssen. In der Regel würden Sie eine Sperre Richtlinie verwenden, um zu verhindern, Benutzer oder Entwickler von begehen versehentlich auf die gleiche Weise, dass Sie eine Variable deklarieren, können die beabsichtigte Verwendung des eine DSL `private`.  
  
 Eine Sperre Richtlinie können auch Sperren für alle Elemente abhängig von der Typ des Elements festgelegt. Grund hierfür ist, `SetLocks(Locks.None)` wird immer aufgerufen, wenn ein Element erstellt wird oder aus der Datei deserialisiert.  
  
 Allerdings können nicht Sie eine Richtlinie verwenden, um die Sperren auf einem Element während seiner Lebensdauer zu verändern. Um diesen Effekt zu erzielen, verwenden Sie Aufrufe von `SetLocks()`.  
  
 Um eine Richtlinie Sperren zu definieren, müssen Sie:  
  
-   Erstellen Sie eine Klasse, die das <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> implementiert.  
  
-   Fügen Sie dieser Klasse auf die Dienste, die über die DocData des der DSL verfügbar sind.  
  
### <a name="to-define-a-locking-policy"></a>So definieren Sie eine Richtlinie Sperre  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>ist wie folgt definiert:  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 Diese Methoden werden aufgerufen, wenn ein Aufruf `SetLocks()` für eine Store, Partitions- oder Modellelement. In jeder Methode auf werden Sie mit einem vorgeschlagenen Satz von Sperren bereitgestellt. Sie können den vorgeschlagenen Satz zurückgeben, oder Sie Addition und Subtraktion von Sperren können.  
  
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
  
 Um sicherzustellen, dass Benutzer immer löschen können Codeelemente, auch wenn andere Aufrufe`SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 Zum Ändern der Eigenschaften aller Elemente der MyClass nicht zulassen:  
  
 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`  
  
### <a name="to-make-your-policy-available-as-a-service"></a>Um Ihre Richtlinie als Dienst verfügbar zu machen  
 In Ihrem `DslPackage` Projekt, fügen Sie eine neue Datei, die Code enthält, die das folgende Beispiel ähnelt:  
  
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
