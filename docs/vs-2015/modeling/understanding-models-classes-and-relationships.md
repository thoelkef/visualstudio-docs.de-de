---
title: Grundlegendes zu Modellen, Klassen und Beziehungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
ms.assetid: 2ecd569c-b369-41ea-b78e-a61b62e2e4e9
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d4381edb42e2aef53c00aea619eea34ee20060d5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424328"
---
# <a name="understanding-models-classes-and-relationships"></a>Grundlagen von Modellen, Klassen und Beziehungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine domänenspezifische Sprache (DSL) wird durch die DSL-Definitionsdatei, zusammen mit benutzerdefinierten Programmcode definiert, die Sie schreiben können. Die meisten der Programmcode in der DSL-Projektmappe wird aus dieser Datei generiert.  
  
 In diesem Thema wird erläutert, die zentralen Funktionen von der DSL-Definition.  
  
## <a name="the-dsl-definition"></a>Der DSL-Definition  
 Beim Öffnen `Dsl\DslDefinition.dsl`, Ihrer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Fenster ähnelt die folgende Abbildung.  
  
 ![DSL-Designer](../modeling/media/dsl-designer.png "DSL-Designer")  
  
 Die wichtigste Informationen in der DSL-Definition wird in der DSL-Definitionsdiagramm angezeigt. Zusätzliche Informationen, die auch "DslDefinition.DSL" gehört, wird im DSL-Explorer angezeigt, die in der Regel auf der Seite des Diagramms angezeigt wird. Sie arbeiten mit dem Diagramm für die häufigsten Aufgaben und DSL-Explorer zum erweiterten Anpassung.  
  
 DSL-Definitionsdiagramm zeigt Domänenklassen, die definieren, Modellelemente und deren Beziehungen, die Verknüpfungen zwischen Modellelementen definieren. Es zeigt auch, Formen und Konnektoren, die verwendet werden, um die Modellelemente, die dem Benutzer anzuzeigen.  
  
 ![DSL-Designer mit Swimlane](../modeling/media/dsl-desinger.png "DSL-Designer")  
  
 Bei Auswahl ein Elements in der DSL-Definition im Diagramm oder im DSL-Explorer wird die Informationen im Fenster Eigenschaften angezeigt. Weitere Informationen können im DSL-Details-Fenster angezeigt werden.  
  
### <a name="models-are-instances-of-dsls"></a>Modelle sind Instanzen der DSLs  
 Ein *Modell* ist eine Instanz Ihrer DSL, die von einem Benutzer erstellt. Ein Modell enthält Modellelemente, die Instanzen von Domänenklassen, die Sie definieren und Links zwischen den Elementen, die Instanzen des domänenbeziehungen sind, die Sie definieren. Auch kann ein Modell verfügen, Formen und Konnektoren, bei die die Modellelemente und Links in einem Diagramm angezeigt. Die DSL-Definition enthält die Formklassen, konnektorklassen und eine Klasse für das Diagramm.  
  
 Eine DSL-Definition ist auch bekannt als eine *Domänenmodell*. Ein DSL-Definition oder Domäne-Modell ist der domänenspezifischen Sprache, die während der Entwurfszeit-Darstellung, während das Modell die Laufzeitinstanziierung der domänenspezifischen Sprache ist.  
  
## <a name="domain-classes-define-model-elements"></a>Domänenklassen definieren Modellelemente  
 Domänenklassen werden verwendet, um die verschiedenen Elemente in der Domäne zu erstellen, und Beziehungen werden die Verknüpfungen zwischen den Elementen. Es handelt sich um die Entwurfszeit-Darstellung der Elemente und Links, die von den Benutzern der Design-spezifischen Sprache instanziiert wird, wenn sie ihre Modelle erstellen.  
  
 Diese Abbildung zeigt ein Modell, das durch den Benutzer eine Musikbibliothek DSL erstellt wurde. Alben werden durch Felder dargestellt, die Listen von Songs enthalten. Künstler nach Feldern mit abgerundeten Ecken dargestellt werden und verbunden sind, mit den Alben, zu denen sie beigetragen haben.  
  
 ![Instanzmodell für generierte DSL](../modeling/media/music-instance.png "Music_Instance")  
  
 Der DSL-Definition werden zwei Aspekte getrennt. Die Darstellung der Modellelemente im Modelldiagramm wird mithilfe von Form und Connector-Klassen definiert. Im Modell enthaltenen Informationen wird mithilfe von Domänenklassen und Beziehungen definiert.  
  
 Die folgende Abbildung zeigt die Domänenklassen und Beziehungen in der DSL-Definition von der Bibliothek "Musik".  
  
 ![Einbetten von und verweisen auf Beziehungen](../modeling/media/music-classes.png "Music_Classes")  
  
 Die Abbildung zeigt vier Domänenklassen: Musik, Album, Künstler und "Song". Die Domänenklassen definieren Domäneneigenschaften wie Name, Titel und So weiter. Im Modell werden die Werte für einige dieser Eigenschaften im Diagramm angezeigt.  
  
 Sind Sie Beziehungen zwischen den Klassen: MusicHasAlbums, MusicHasArtists, AlbumbHasSongs, and ArtistAppearedOnAlbums. Die Beziehungen haben Multiplizitäten wie z. B. 1..1, 0.. *. Beispielsweise muss jeder "Song" mit genau einem Album über die AlbumHasSongs-Beziehung verknüpft sein. Jedes Album kann es sich um eine beliebige Anzahl von Songs verfügen.  
  
### <a name="rearranging-the-dsl-definition-diagram"></a>Neuanordnen von DSL-Definitionsdiagramm  
 Beachten Sie, dass eine Domänenklasse mehrmals auf die DSL-Definitionsdiagramm angezeigt werden kann, wie das Album in dieser Abbildung ist. Es gibt immer eine Hauptansicht, und es kann einige *Verweis* Ansichten.  
  
 Um die DSL-Definitionsdiagramm neu anzuordnen, können Sie folgende Aktionen ausführen:  
  
- Main wechseln und auf Ansichten können Sie mit der **Struktur hier** und **Baum teilen** Befehle. Mit der rechten Maustaste in einer einzelne Domäne-Klasse, um diese Befehle finden Sie unter.  
  
- Neu anordnen von Domänenklassen und Formklassen durch Drücken von STRG + nach-oben und STRG + nach-unten.  
  
- Klassen, die mithilfe des Symbols auf der rechten oberen Ecke der einzelnen Formen erweitern oder reduzieren.  
  
- Reduzieren Sie Teile der Struktur, indem Sie auf das Minuszeichen (-) am unteren Rand einer Domänenklasse.  
  
## <a name="inheritance"></a>Vererbung  
 Domänenklassen können unter Verwendung der Vererbung definiert werden. Um eine Ableitung von Vererbung zu erstellen, klicken Sie auf das Tool Vererbung, klicken Sie auf die abgeleitete Klasse, und klicken Sie dann auf die Basisklasse. Ein Element des Modells hat alle Eigenschaften, die auf ihrer eigenen Domänenklasse, zusammen mit den Eigenschaften, die für die von der Basisklasse geerbt definiert sind. Es erbt auch die Rollen in Beziehungen.  
  
 Vererbung kann auch zwischen den Beziehungen, Formen und Connectors verwendet werden. Vererbung muss innerhalb der gleichen Gruppe beibehalten. Eine Form kann nicht von einer Domänenklasse erben.  
  
## <a name="domain-relationships"></a>Domänenbeziehungen  
 Modellelemente können durch Beziehungen verknüpft werden. Links werden immer binäre; Sie enthalten genau zwei Elemente links. Allerdings ein Element haben viele Links zu anderen Objekten, und es kann mehr als eine Verknüpfung zwischen demselben Paar von Elementen.  
  
 Ebenso, wie Sie verschiedene Klassen von Elementen definieren können, können Sie andere Klassen von Links definieren. Die Klasse einer Verknüpfung wird aufgerufen, eine *domänenbeziehung*. Eine domänenbeziehung gibt an, welche Klassen von Elementen für die Instanzen eine Verbindung herstellen können. Jedes Ende einer Beziehung wird aufgerufen, eine *Rolle*, und die domänenbeziehung definiert Namen für die beiden Rollen sowie für die Beziehung selbst.  
  
 Es gibt zwei Arten des domänenbeziehungen: Einbetten von Beziehungen und verweisbeziehungen. Klicken Sie auf die DSL-Definitionsdiagramm einbettende Beziehungen haben durchgezogene Linien auf jede Rolle und verweisbeziehungen haben gestrichelte Linien.  
  
### <a name="embedding-relationships"></a>Einbetten von Beziehungen  
 Jedes Element in einem Modell, mit Ausnahme von Stamm, ist das Ziel einer einbettenden links. Aus diesem Grund bildet das gesamte Modell eine einzelne Struktur einbettender Links. Eine einbettende Beziehung stellt die Kapselung oder des Besitzes dar. Zwei Modellelementen, die auf diese Weise beziehen sind auch bekannt als übergeordnete und untergeordnete. Das untergeordnete Element wird als im übergeordneten Element eingebettet werden.  
  
 Einbetten von Links werden nicht in der Regel explizit als Connectors in einem Diagramm angezeigt. Stattdessen werden sie in der Regel durch Einschluss dargestellt. Der Stamm des Modells wird im Diagramm dargestellt, und eingebettete Elemente werden als Formen im Diagramm angezeigt.  
  
 Im Beispiel ist die Stammklasse Musik eine einbettende Beziehung MusicHasAlbums Album, die ein einbetten AlbumHasSongs auf "Song" verfügt. Titel werden als Elemente in einer Liste in jedes Album angezeigt. Musik verfügt auch über eine einbettende MusicHasArtists der Interpret-Klasse, deren Instanzen auch als Formen im Diagramm angezeigt werden.  
  
 Standardmäßig werden die eingebetteten Elemente automatisch gelöscht, wenn ihren übergeordneten Elementen gelöscht werden.  
  
 Wenn ein Modell gespeichert wird in Form von XML-Datei, eingebettete Elemente geschachtelt sind innerhalb von übergeordneten Elementen, es sei denn, Sie die Serialisierung angepasst haben.  
  
> [!NOTE]
> Einbettung ist nicht identisch mit Vererbung. Untergeordnete Elemente in einer einbettenden Beziehung erben keine Eigenschaften des übergeordneten Elements. Eine Einbettung ist eine Art von Verknüpfung zwischen Modellelementen. Vererbung ist eine Beziehung zwischen Klassen und erstellt keine Verknüpfungen zwischen Modellelementen.  
  
### <a name="embedding-rules"></a>Einbetten von Regeln  
 Jedes Element in einem instanzenmodell muss es sich um das Ziel des genau eine einbettende links, mit Ausnahme der Stamm des Modells sein.  
  
 Aus diesem Grund jede nicht abstrakte Domänenklasse mit Ausnahme der Stammklasse muss Ziel mindestens einer einbettenden Beziehung sein, oder eine Einbettung von einer Basisklasse erben müssen. Eine Klasse kann das Ziel der einbettungen von zwei oder mehr sein, aber die Modellelemente Instanz können nur ein übergeordnetes Element zu einem Zeitpunkt aufweisen. Die Multiplizität von Ziel zu Quelle muss 0.. 1 "oder" 1..1 sein.  
  
### <a name="the-explorer-displays-the-embedding-tree"></a>Der Explorer zeigt die einbettende Struktur  
 Ihrer DSL-Definition erstellt auch einen Explorer, der Benutzer zusammen mit ihren Modelldiagramm finden Sie unter.  
  
 ![Generierter Explorer für DSL](../modeling/media/music-explorer.png "Music_Explorer")  
  
 Der Explorer zeigt alle Elemente im Modell, auch solche, die für die Sie keine Formen definiert haben. Es zeigt Elemente und einbettenden Beziehungen, aber nicht auf Beziehungen verweisen.  
  
 Um die Werte der Domäneneigenschaften eines Elements anzuzeigen, der Benutzer wählt ein Element, in dem Modelldiagramm oder im Modell-Explorer, und öffnet das Fenster Eigenschaften. Alle werden die Domäneneigenschaften angezeigt, einschließlich derjenigen, die nicht im Diagramm angezeigt werden. Im Beispiel jedes "Song" hat, einem Titel und ein Genre, aber nur der Wert des Titels im Diagramm angezeigt.  
  
## <a name="reference-relationships"></a>Verweisbeziehungen  
 Eine verweisbeziehung stellt jede Art von Beziehung, die nicht eingebettet ist.  
  
 Verweisbeziehungen werden in der Regel in einem Diagramm als Connectors zwischen Formen angezeigt.  
  
 In der XML-Darstellung des Modells wird ein Link zwischen zwei Elementen dargestellt, mit *Moniker.* D. h. sind Moniker Namen, die jedes Element im Modell eindeutig zu identifizieren. Der XML-Knoten für jedes Modellelement enthält einen Knoten, der den Namen der Beziehung und den Moniker des anderen Elements angibt.  
  
## <a name="roles"></a>Rollen  
 Jede domänenbeziehung verfügt über zwei Rollen, eine Quelle und ein Zielrolle.  
  
 In der folgenden Abbildung ist die Linie zwischen den **Verleger** Domänenklasse und der **PublisherCatalog** domänenbeziehung ist die Quellrolle. Die Linie zwischen der domänenbeziehung und der **Album** Domänenklasse wird die Zielrolle.  
  
 ![Rollen und Eigenschaften. ](../modeling/media/propertycode.png "PropertyCode")  
  
 Die Namen einer Beziehung sind besonders wichtig, wenn Sie Programmcode schreiben, der das Modell durchläuft. Z. B. Wenn Sie die DSL-Projektmappe erstellen, hat die generierte Klasse Verleger, eine Eigenschaft enthalten, der eine Auflistung von Alben ist. Die Klasse Album hat es sich um eine Eigenschaft Herausgeber an, der eine einzelne Instanz der Publisher-Klasse ist.  
  
 Wenn Sie eine Beziehung in einer DSL-Definition erstellen, werden die Namen der Eigenschaft und die Beziehung Standardwerte angegeben. Allerdings können Sie diese ändern.  
  
## <a name="multiplicities"></a>Multiplizitäten  
 Multiplizitäten anzugeben, wie viele Elemente in einer domänenbeziehung dieselbe Rolle haben. Im Beispiel, das 0 (null): n-(0..\*) Multiplizität-Einstellung für die **Katalog** Rolle angibt, die einer beliebigen Instanz von der **Verleger** Domänenklasse lassen sich so viele  **PublisherCatalog** Beziehung verknüpft, als es erhalten sollen.  
  
 Die Multiplizität einer Rolle zu konfigurieren, indem Sie auf das Diagramm eingeben oder durch Ändern der `Multiplicity` -Eigenschaft in der **Eigenschaften** Fenster. Die folgende Tabelle beschreibt die Einstellungen für diese Eigenschaft.  
  
|Multiplicity-Typ|Beschreibung|  
|-----------------------|-----------------|  
|0.. * (0 bis n)|Jede Instanz der Domänenklasse kann es sich um mehrere Instanzen der Beziehung oder keine Instanzen der Beziehung aufweisen.|  
|0.. 1 (0 bis)|Jede Instanz der Domänenklasse kann es sich um nicht mehr als eine Instanz der Beziehung oder keine der Instanzen der Beziehung aufweisen.|  
|1..1 (eins)|Jede Instanz der Domänenklasse kann es sich um eine Instanz der Beziehung aufweisen. Sie können nicht mehr als eine Instanz der Beziehung von jeder Instanz der Role-Klasse erstellen. Wenn die Validierung aktiviert ist, wird ein Validierungsfehler angezeigt, wenn Instanz der Role-Klasse keine Instanz der Beziehung hat.|  
|1.. * (eins zu viele)|Jede Instanz der Klasse für die Rolle, die diese Multiplizität kann mehrere Instanzen der Beziehung, und jede Instanz muss über mindestens eine Instanz der Beziehung verfügen. Wenn die Validierung aktiviert ist, wird ein Validierungsfehler angezeigt, wenn Instanz der Role-Klasse keine Instanz der Beziehung hat.|  
  
## <a name="domain-relationships-as-classes"></a>Domänenbeziehungen als Klassen  
 Ein Link wird in den Store als eine Instanz von LinkElement, dargestellt, die eine von ModelElement abgeleitete Klasse ist. Sie können diese Eigenschaften in der Domäne Modelldiagramm auf domänenbeziehungen definieren.  
  
 Sie können auch die Quelle oder Ziel für andere Beziehungen einer Beziehung machen. In dem Modelldiagramm Domäne, mit der rechten Maustaste der domänenbeziehung, und klicken Sie dann auf **als Klasse anzeigen**. Eine weitere Klasse angezeigt. Sie können Beziehungen dann damit verbinden.  
  
 Sie können teilweise durch Vererbung, eine Beziehung definieren, ebenso wie mit Domänenklassen. Wählen Sie die abgeleitete Beziehung, und legen Sie **Base Beziehung** im Eigenschaftenfenster angezeigt.  
  
 Eine abgeleitete Beziehung spezialisiert auf seine Basisklasse Beziehung. Die Domäne Klassen, die It, die Links von abgeleitet werden sollte oder die gleiche wie die Klassen, die von der Basisklasse Beziehung verknüpft. Wenn eine Verknüpfung der abgeleiteten Beziehung in einem Modell erstellt wird, ist es eine Instanz der abgeleiteten und basisbeziehungen. Im Programmcode können Sie sich an das andere Ende der Verknüpfung mit den Eigenschaften, die von den Basis- oder von der abgeleiteten Klasse generiert navigieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Domänenbeziehungen in der generierten API](../misc/domain-relationships-in-the-generated-api.md)   
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
