---
title: Standardstereotype für UML-Modellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML, stereotypes
- UML diagrams, stereotypes
ms.assetid: 8a8c2321-1cae-4ba8-bb9e-23495c3404d8
caps.latest.revision: 22
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3e5cabed5b2b75d9a97c74dd58d87ea387df8f8e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514713"
---
# <a name="standard-stereotypes-for-uml-models"></a>Standardstereotype für UML-Modelle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Standardstereotype für UML-Modelle](https://docs.microsoft.com/visualstudio/modeling/standard-stereotypes-for-uml-models).  
  
Sie können Stereotype zu UML-Modellelementen hinzufügen, um zusätzliche Informationen für den Leser oder für die maschinelle Verarbeitung bereitzustellen. Stereotype werden in Profilen definiert, und jedes Profil stellt Sätze von Stereotypen bereit. In Visual Studio werden mehrere Profile bereitgestellt. Sie können auch eigene Profile definieren, die eigene Stereotype enthalten können. Weitere Informationen finden Sie unter [Definieren eines Profils zum Erweitern von UML](../modeling/define-a-profile-to-extend-uml.md).  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="the-standard-profiles"></a>Die Standardprofile  
 Die folgenden Profile sind in einer unterstützten Version von Visual Studio verfügbar, sobald Sie es installiert haben.  
  
|Profile|Zweck|  
|-------------|-------------|  
|[UML-Standardprofil L2](#L2)|Ein Standardsatz von Stereotypen, die verwendet werden können, um zusätzliche Informationen über ein Element oder eine Beziehung hinzuzufügen.|  
|[UML-Standardprofil L3](#L3)|Ein Standardsatz von Stereotypen, die verwendet werden können, um zusätzliche Informationen über ein Element oder eine Beziehung hinzuzufügen.|  
|[C#-Profil](#NetProfile)|Wenn eine Klasse oder ein anderes Element in einem UML-Modell Programmcode darstellen soll, können Sie dies angeben, indem Sie eines der Stereotype aus dem C#-Profil anwenden.<br /><br /> Mit diesen Stereotypen werden außerdem den Modellelementen Eigenschaften hinzugefügt.|  
  
 Wenn Sie ein neues UML-Modell erstellen, werden die UML-Standardprofile L2 und L3 mit dem Modell verknüpft, es sei denn, Sie entfernen die Links.  
  
 Um die Stereotype in einem dieser Profile zu verwenden, müssen Sie zuerst das Profil mit einem Paket oder einem Modell verknüpfen, das die Elemente enthält, auf die Sie sie anwenden möchten.  
  
#### <a name="to-link-a-profile-to-a-model-or-a-package"></a>So verknüpfen Sie ein Profil mit einem Modell oder einem Paket  
  
1.  Open **UML-Modell-Explorer**. Auf der **Architektur** Startmenü **Windows**, und klicken Sie dann auf **UML-Modell-Explorer**.  
  
2.  Suchen Sie ein Paket oder ein Modell, das alle Elemente enthält, auf die Sie die Stereotype im Profil anwenden möchten.  
  
3.  Mit der rechten Maustaste das Paket oder das Modell, und klicken Sie dann auf **Eigenschaften**.  
  
4.  In der **Eigenschaften** legen die **Profile** Eigenschaft, um die gewünschten Profile fest.  
  
#### <a name="to-remove-the-link-between-a-profile-and-a-model-or-package"></a>So entfernen Sie den Link zwischen einem Profil und einem Modell oder einem Paket  
  
1.  Klicken Sie im UML-Modell-Explorer mit der rechten Maustaste das Modell oder Paket, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Legen Sie im Fenster Eigenschaften die **Profile** als leere Eigenschaft.  
  
    > [!NOTE]
    >  Sie können die Verknüpfung eines Profils nur aufheben, wenn keines der Elemente im Modell oder Paket die Stereotype dieses Profils verwendet.  
  
#### <a name="to-apply-a-stereotype-to-a-model-element"></a>So wenden Sie ein Stereotyp auf ein Modellelement an  
  
1.  Mit der rechten Maustaste in des Modellelements in einem Diagramm oder im **UML-Modell-Explorer**, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **Stereotype** Eigenschaft, und wählen Sie die Stereotype, die Sie anwenden möchten.  
  
     Für die meisten Arten von Elementen werden die ausgewählten Stereotype innerhalb von Chevrons (« ») im Modellelement angezeigt.  
  
    > [!NOTE]
    >  Wenn Sie nicht sehen können die **Stereotype** -Eigenschaft, oder wenn das gewünschte Stereotyp nicht angezeigt wird, stellen Sie sicher, dass das Modellelement in einem Paket oder ein Modell ist, das entsprechende Profil verknüpft wurde.  
  
3.  Einige Stereotype ermöglichen es Ihnen, die Werte zusätzlicher Eigenschaften für das Modellelement festzulegen. Um diese Eigenschaften anzuzeigen, erweitern Sie die **Stereotype** Eigenschaft.  
  
###  <a name="L2"></a> UML-Standardprofil L2  
 Die folgenden Stereotype können verwendet werden, um die spezifische Bedeutung von UML-Modellelementen anzugeben, es sei denn, der Link zum Profil wurde aus dem Modell entfernt.  
  
 Die genaue Bedeutung dieser Stereotype wird durch die lokalen Konventionen bestimmt, sowie ggf. durch Tools, mit denen Sie möglicherweise das Modell verarbeiten.  
  
|Stereotyp|Betrifft|Bedeutung|  
|----------------|----------------|-------------|  
|auxiliary|Klasse|Eine Klasse, die eine andere Klasse unterstützt, in der Regel durch das Implementieren von zusätzlicher Logik. Die andere Klasse kann über das Stereotyp «focus» verfügen.|  
|call|Abhängigkeit|Die Clientklasse ruft die Vorgänge des Lieferanten auf.|  
|create|Abhängigkeit|Die Clientklasse erstellt Instanzen des Lieferanten.|  
|create|Nachricht|Der Absender erstellt den Empfänger.|  
|create|Vorgang|Dieser Vorgang ist ein Konstruktor.|  
|derive|Abhängigkeit|Das Clientelement wird vollständig oder teilweise aus dem Lieferanten berechnet.|  
|destroy|Vorgang|Der Vorgang zerstört seine Instanz.|  
|document|Artefakt|Ein «file», das keine Quelle und keine ausführbare Datei ist.|  
|entity|Komponente|Die Komponente stellt ein Geschäftskonzept dar.|  
|executable|Artefakt|Ein ausführbares «file».|  
|Datei|Artefakt|Eine physische Datei|  
|focus|Klasse|Eine Klasse, die die Kerngeschäftslogik definiert, die von mehreren «auxiliary»-Klassen unterstützt wird.|  
|framework|Package|Dieses Paket definiert ein wiederverwendbares Entwurfsmuster.|  
|implement|Komponente|Die Implementierung einer «specification».|  
|implementationClass|Klasse|Die Klasse beschreibt eine Implementierung, und jede Laufzeitinstanz verfügt über eine feste Implementierungsklasse. Gegensatz zu «type».|  
|instantiate|Abhängigkeit|Der Client erstellt Instanzen des Lieferanten.|  
|library|Artefakt|Ein Bibliotheks-«file».|  
|metaclass|Klasse|Instanzen dieser Klasse sind ebenfalls Klassen.|  
|modelLibrary|Package|Enthält Modellelemente, die durch das Importieren von Paketen wiederverwendet werden sollen. In der Regel als Teil eines Profils definiert und durch Anwenden des Profils automatisch importiert.|  
|process|Komponente|Eine transaktionsbasierte Komponente oder eine Komponente mit einem Thread.|  
|realization|Klasse, Schnittstelle, Komponente|Beschreibe eine Implementierung.|  
|refine|Abhängigkeit|Die Clientklasse, die Komponente oder das Paket stellt mehr Informationen über die Spezifikation oder den Entwurf bereit als der Lieferant.|  
|responsibility|Abhängigkeit|Der Kommentar am Lieferantenende der Abhängigkeit definiert die Zuständigkeiten der Clientklasse oder der Komponente.|  
|script|Artefakt|Ein interpretierbares «file».|  
|send|Abhängigkeit|Der Quellvorgang sendet das Zielsignal.|  
|service|Komponente|Eine zustandslose Komponente.|  
|Quelle|Artefakt|Ein kompilierbares «file».|  
|specification|Klasse, Schnittstelle, Komponente|Definiert das Verhalten einer Komponente oder eines Objekts, ohne die interne Funktionsweise zu definieren.|  
|subsystem|Komponente|Ein Teil eines umfangreichen Systems. Ein Subsystem in einem Anwendungsfalldiagramm ist eine Komponente mit dem Stereotyp „subsystem“.|  
|trace|Abhängigkeit|Das Clientelement ist Teil des Entwurfs für die Realisierung des Lieferanten. Die beiden Enden dieser Abhängigkeit befinden sich in der Regel in unterschiedlichen Modellen. Das eine Modell ist die Realisierung des anderen Modells.|  
|Typ|Klasse|Gibt das Verhalten eines Objekts an, ohne anzugeben, wie es implementiert wird. Ein Objekt ist ein Member eines Typs, wenn es der Spezifikation entspricht.|  
|utility|Klasse|Eine Auflistung von statischen Funktionen. Die Klasse verfügt über keine Instanzen.|  
  
###  <a name="L3"></a> UML-Standardprofil L3  
 Die folgenden Stereotype können verwendet werden, um die spezifische Bedeutung von UML-Modellelementen anzugeben, es sei denn, die Verknüpfung des Profils mit dem Modell wurde aufgehoben.  
  
 Die genaue Bedeutung dieser Stereotype wird durch die lokalen Konventionen bestimmt, sowie ggf. durch Tools, mit denen Sie möglicherweise das Modell verarbeiten.  
  
|Stereotyp|Betrifft|Beschreibung|  
|----------------|----------------|-----------------|  
|buildComponent|Komponente|Eine Auflistung von Elementen, mit denen ein Build definiert wird.|  
|metaModel|Modell|Definiert eine Modellierungssprache, z. B. eine Variante von UML, oder eine domänenspezifische Sprache.|  
|systemModel|Modell|Ein Modell, bei dem es sich um eine Auflistung von Modellen handelt, die auf das gleiche System angewendet werden, z. B. eine Spezifikation, eine Realisierung, sowie Ablaufverfolgungsbeziehungen zwischen diesen.|  
  
##  <a name="NetProfile"></a> C#-Profil  
 Mit den in diesem Profil definierten Stereotypen können Sie angeben, dass ein Modellelement zur Übersetzung in Programmcode vorgesehen ist. Jedes Stereotyp definiert zusätzliche Eigenschaften, die Sie für das Modellelement festlegen können.  
  
 Um diese Stereotype verfügbar zu machen, verknüpfen Sie ein Modell oder ein Paket mit dem C#-Profil. Sie können dann die Stereotype auf Modellelemente in diesem Modell oder Paket anwenden.  
  
 Die verfügbaren Stereotype, die Elemente, für die sie gelten, und die zusätzlichen Eigenschaften, die sie verfügbar machen, werden in der folgenden Tabelle zusammengefasst.  
  
|Stereotyp|Betrifft|Eigenschaften|  
|----------------|----------------|----------------|  
|**C#-Klasse**|UML-Klasse<br /><br /> Komponente|**CLR-Attribute**<br /><br /> **Ist Partial**<br /><br /> **Ist versiegelt**<br /><br /> **Ist Static**<br /><br /> **Ist Unsafe**<br /><br /> **Paketsichtbarkeit**|  
|**C#-Struktur**|UML-Klasse<br /><br /> Komponente|**CLR-Attribute**<br /><br /> **Ist Partial**<br /><br /> **Ist Unsafe**<br /><br /> **Paketsichtbarkeit**|  
|**Globale C#-Member**|UML-Klasse<br /><br /> Komponente|**CLR-Attribute**|  
|**C#-Schnittstelle**|C#-Schnittstelle|**CLR-Attribute**<br /><br /> **Ist Partial**<br /><br /> **Paketsichtbarkeit**|  
|**C#-Enumeration**|UML-Enumeration|**ClrAttributes**<br /><br /> **Basistyp**|  
|**C#-namespace**|UML-Paket|**CLR-Attribute**<br /><br /> **Basisname**<br /><br /> **Verwenden von namespaces**|  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Stereotypen zu UML-Modellelementen](../modeling/add-stereotypes-to-uml-model-elements.md)   
 [Anpassen des Modells mit Profilen und Stereotypen](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Definieren eines Profils zum Erweitern von UML](../modeling/define-a-profile-to-extend-uml.md)



