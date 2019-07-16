---
title: Glossar der Begriffe zu MSBuild
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e84a7c3c7e402edb3c39ea247ea7efffce1b60df
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154841"
---
# <a name="msbuild-glossary"></a>MSBuild-Glossar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit den folgenden Begriffen werden Microsoft Build Engine (MSBuild) und deren Komponenten beschrieben.

## <a name="glossary"></a>Glossar
 AssemblyFoldersEx

 Ein Registrierungsspeicherort, an dem Drittanbieter Pfade für jede Version des Frameworks speichern, das sie unterstützen, und die Entwurfszeitauflösung nach Verweisassemblys suchen kann.

 Batchverarbeitung

 Batchverarbeitung bedeutet, dass Elemente anhand der Elementmetadaten in als *Batches* bezeichnete Kategorien unterteilt werden, über die anschließend jeweils ein Ziel oder eine Aufgabe ausgeführt wird. Die Batchverarbeitung ist die MSBuild-Entsprechung des Schleifenkonstrukts. Weitere Informationen finden Sie unter [Batching](../msbuild/msbuild-batching.md) (MSBuild-Batchverarbeitung).

 Buildumfang

 Der Buildumfang beschreibt ein MSBuild-Objekt, z. B. eine globale Eigenschaft, das für ein Projekt und ggf. für dessen in einem Build mit mehreren Projekten erstellte untergeordnete Projekte potenziell sichtbar ist.

 untergeordnetes Projekt

 Siehe *Projekt, untergeordnet*.

 Bedingung

 Viele MSBuild-Elemente können bedingt definiert werden, das heißt, im Element wird das `Condition`-Attribut angegeben. Sofern wenn die Bedingung nicht `true` ergibt, wird der Inhalt bedingter Elemente ignoriert. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).

 Definition, Element

 Siehe *Elementdefinition*.

 Ausgabeelement

 Während der Ausführungsphase eines Builds können Elemente von Aufgaben erstellt oder geändert werden, die untergeordnete `Output`-Elemente mit dem `ItemName`-Attribut aufweisen. Die Aufgabe gibt die neuen Elemente sozusagen aus.

 Ausgabeeigenschaft

 Während der Ausführungsphase eines Builds können Eigenschaften von Aufgaben erstellt oder geändert werden, die untergeordnete `Output`-Elemente mit dem `PropertyName`-Attribut aufweisen. Die Aufgabe gibt die neue Eigenschaft sozusagen aus.

 Auswertungsphase

 Als Auswertung wird die erste Phase eines Projektbuilds bezeichnet. Alle Eigenschaften und Elemente werden in der Reihenfolge ausgewertet, in der sie in der Projektdatei angezeigt werden. Importierte Projekte werden ausgewertet, sobald sie im Projekt gefunden wurden. Ziele und Aufgaben werden erst in der Ausführungsphase ausgeführt, und alle Eigenschaften oder Elemente, die sie deklarieren oder ausgeben würden, werden während der Auswertung ignoriert.

 Ausführungsphase

 Die Ausführung bildet die zweite Phase eines Projektbuilds. Ausgewählte Ziele werden erstellt, und Aufgaben werden ausgeführt. Eigenschaften und Elemente können erstellt oder im Vergleich zu den zugehörigen Auswertungswerten geändert werden.

 Funktion, Eigenschaft

 Siehe *Eigenschaftenfunktion*.

 Funktion, Element

 Siehe Elementfunktion.

 Element

 Elemente bilden Eingaben für das Buildsystem und werden auf Grundlage ihrer Elementnamen in Elementtypen gruppiert. Elemente stellen in der Regel Dateien dar. Da Elemente anhand des Elementtyps benannt werden, zu dem sie gehören, können die Begriffe *Element* und *Elementwert* synonym verwendet werden. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).

 Elementdefinition

 Elementdefinitionsgruppen enthalten Elementdefinitionen, durch die jedem Elementtyp Standardmetadaten hinzugefügt werden. Analog zu bekannten Metadaten sind die Standardmetadaten allen Elementen des angegebenen Elementtyps zugeordnet. Standardmetadaten können in einer Elementdefinition explizit überschrieben werden. Weitere Informationen finden Sie unter [Item Definitions](../msbuild/item-definitions.md) (Elementdefinitionen).

 Elementfunktion

 Elementfunktionen rufen Informationen über die Elemente im Projekt ab. Diese Funktionen vereinfachen das Abrufen von Distinct()-Elementen, und mit ihnen erfolgt der Abruf schneller als beim Durchlaufen der Elemente. Es gibt Funktionen zum Bearbeiten von Elementpfaden und -zeichenfolgen. Weitere Informationen finden Sie unter [Item Functions](../msbuild/item-functions.md) (Elementfunktionen).

 Elementmetadaten

 Siehe *Metadaten, Element*.

 Elementtyp

 Elementtypen sind benannte Listen von Elementen, die als Parameter für Aufgaben verwendet werden können. In den Aufgaben werden die Schritte des Buildprozesses mithilfe der Elementwerte ausgeführt. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).

 Metadaten, Element

 Elementmetadaten sind Auflistungen von Name-Wert-Paaren, die einem Element zugeordnet sind. Metadaten enthalten beschreibende Informationen zum Element und sind, außer bei bekannten Metadaten, optional. Weitere Informationen finden Sie unter [Items](../msbuild/msbuild-items.md) (MSBuild-Elemente).

 Metadaten, bekannte

 Als bekannte Metadaten werden schreibgeschützte Elementmetadaten bezeichnet, die mit einem vordefinierten Wert initialisiert werden. Bekannte Metadaten enthalten beschreibende Informationen zu einem Element, das auf eine Datei verweist. Beispielsweise wird als Wert des bekannten Metadatenelements `FullPath` der vollständige Pfad der Datei verwendet, auf die verwiesen wird. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).

 Festlegung von Zielversionen

 Die Fähigkeit eines Anwendungs- oder Assemblyprojekts, auf viele verschiedene CLRs und Frameworks von MSBuild und Visual Studio abzuzielen.

 Profil

 Eine Teilmenge des vollständigen Frameworks. Dies wird verwendet, um die Menge zu verringern, die auf einen Computer heruntergeladen werden muss.

 Projektdatei

 Eine Projektdatei enthält das MSBuild-Skript, das den Build steuert. Projektdateien weisen meist eine Dateierweiterung auf, die mit "proj" endet, z. B. .csproj oder .vbproj. Von Projektdateien können Eigenschaftendateien und Zieldateien importiert werden.

 property

 Eine Eigenschaft besteht aus einem Schlüssel-Wert-Paar, das zum Steuern des Buildprozesses verwendet wird. Weitere Informationen finden Sie unter [MSBuild Properties](msbuild-properties1.md) (MSBuild-Eigenschaften).

 Eigenschaft, Umgebung

 Umgebungseigenschaft wird eine Eigenschaft genannt, die automatisch mit dem Wert einer Systemumgebungsvariable mit demselben Namen initialisiert wird. Weitere Informationen finden Sie unter [MSBuild Properties](msbuild-properties1.md) (MSBuild-Eigenschaften).

 Eigenschaftendatei

 Als Eigenschaftendatei wird eine Projektdatei bezeichnet, die vor allem Eigenschaftengruppen und Elementgruppen zur Steuerung des Builds enthält. Üblicherweise besitzen solche Dateien die Dateierweiterung .props. Eigenschaftendateien werden meist am Anfang zugeordneter Projektdateien importiert.

 Eigenschaft, Funktion

 Als Eigenschaftenfunktion wird eine Systemeigenschaft oder -methode bezeichnet, die zum Auswerten von MSBuild-Skripts verwendet werden kann. Mit Eigenschaftenmethoden ist es möglich, die Systemzeit zu lesen, Zeichenfolgen zu vergleichen, nach regulären Ausdrücke zu suchen und weitere Aktionen auszuführen. Weitere Informationen finden Sie unter [Property Functions](../msbuild/property-functions.md) (Eigenschaftenfunktionen).

 Eigenschaftenfunktion, geschachtelt

 Eigenschaftenfunktionen können zu komplexeren Funktionen kombiniert werden. Ein auf ein Objekt angewendeter

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

 Weitere Informationen finden Sie unter [Property Functions](../msbuild/property-functions.md) (Eigenschaftenfunktionen).

 Eigenschaft, global

 Eine globale Eigenschaft besteht aus einem Schlüssel-Wert-Paar, das zum Steuern des Buildprozesses verwendet wird. Globale Eigenschaften werden an einer Eingabeaufforderung oder über das `Properties`-Attribut einer [MSBuild-Aufgabe](../msbuild/msbuild-task.md) festgelegt und können während der Auswertungsphase eines Builds nicht geändert werden. Weitere Informationen finden Sie unter [MSBuild Properties](msbuild-properties1.md) (MSBuild-Eigenschaften).

 Eigenschaft, lokal

 Eine lokale Eigenschaft besteht aus einem Schlüssel-Wert-Paar, das zum Steuern des Buildprozesses verwendet wird. Dieser Begriff wird nur verwendet, um explizit eine Eigenschaft zu bezeichnen, bei der es sich um keine globale Eigenschaft handelt.

 Eigenschaft, Registrierung

 Registrierungseigenschaften besitzen einen Wert, der mit einer besonderen Syntax festgelegt wird, die den Wert eines Systemregistrierungsunterschlüssels liest. Weitere Informationen finden Sie unter [MSBuild Properties](msbuild-properties1.md) (MSBuild-Eigenschaften).

 Eigenschaft, reserviert

 Eine reservierte Eigenschaft besteht aus einem Schlüssel-Wert-Paar, das zum Steuern des Buildprozesses verwendet wird. Reservierte Eigenschaften werden automatisch mit vordefinierten Werten initialisiert. Weitere Informationen finden Sie unter [MSBuild Properties](msbuild-properties1.md) (MSBuild-Eigenschaften).

 Projektumfang

 Der Projektumfang beschreibt ein MSBuild-Objekt, z. B. eine lokale Eigenschaft, das nur in der enthaltenden Projektdatei und in allen Projekten sichtbar ist, die von dieser importiert wurden.

 Projekt, untergeordnetes

 Ein untergeordnetes Projekt wird während eines Projektbuilds von der MSBuild-Aufgabe erstellt. Dieses neue Projekt ist dem Projekt untergeordnet, das das Ziel mit der MSBuild-Aufgabe enthält oder importiert. Das untergeordnete Projekt erbt die globalen Eigenschaften des übergeordneten Projekts, sofern diese nicht vom `Properties`-Attribut geändert werden.

 redist-Liste

 Neuverteilungsliste: die Liste der Assemblys, die einem angegebenen Framework entsprechen.

 Verweisassembly

 Eine Assembly, mit der während der Entwurfszeit eine Anwendung erstellt wird. Von einer Verweisassembly können der tatsächliche Code und die privaten Schnittstellen entfernt und nur die Metadaten und die öffentlichen Schnittstellen beibehalten werden.

 Registrierungseigenschaft

 Siehe *Eigenschaft, Registrierung*.

 target

 In einem Ziel werden Aufgaben in einer bestimmten Reihenfolge gruppiert und Abschnitte der Projektdatei als Einstiegspunkte in den Buildprozess verfügbar gemacht. Weitere Informationen finden Sie unter [Targets](../msbuild/msbuild-targets.md) (MSBuild-Ziele).

 Ziel, Build

 Siehe Ziel, Ausführen.

 Ziel, Auswerten

 Aufgrund der inkrementellen Kompilierung müssen Ziele auf potenzielle Änderungen an Eigenschaften und Elementen analysiert werden. Diese Änderungen müssen auch vorgenommen werden, wenn das Ziel übersprungen wurde. Ein Ziel auszuwerten bedeutet, diese Analyse auszuführen und die genannten Änderungen vorzunehmen. Weitere Informationen finden Sie unter [Incremental Builds](../msbuild/incremental-builds.md) (Inkrementelle Builds).

 Ziel, Ausführen (Execute)

 Ein Ziel auszuführen bedeutet, dieses auszuwerten und alle Aufgaben auszuführen, die keine Bedingungen aufweisen oder deren Bedingungen zu true ausgewertet werden. Während der inkrementellen Kompilierung können Ziele übersprungen oder ausgeführt werden, jedoch werden sie werden in jedem Fall ausgewertet. Weitere Informationen finden Sie unter Ziel, Auswerten.

 Ziel, Ausführen (Run)

 Ein Ziel, das eine Bedingung aufweist, die false ergibt, wird nicht ausgeführt (Run) und besitzt daher keine Auswirkungen auf den Build. Ziele, die ausgeführt (Run) werden, werden ausgeführt (Execute) oder aber übersprungen. In jedem Fall wird das Ziel ausgewertet. Weitere Informationen finden Sie unter Ziel, Auswerten.

 Ziel, Überspringen

 Wenn bei der inkrementellen Kompilierung ermittelt wird, dass alle Ausgabedateien aktuell sind, wird das Ziel übersprungen, das heißt, das Ziel wird ausgewertet, jedoch werden die Aufgaben im Ziel nicht ausgeführt. Weitere Informationen finden Sie unter Ziel, Auswerten.

 Zielframeworkmoniker

 Ein Name, der das Framework (z. B. .NET Framework, Silverlight usw.), die Version und das Profil (z. B. Client, Server usw.) beschreibt, auf die/das abgezielt werden soll.

 Paket zur Festlegung von Zielversionen

 Die Liste der Assemblys, die mit einem angegebenen Framework und dem Satz von Verweisassemblys für dieses Framework verteilt werden sollen.

 TARGETS-Datei

 Eine TARGETS-Datei ist eine Projektdatei, die vor allem Ziele und Aufgaben zur Steuerung des Builds enthält. Üblicherweise besitzen solche Dateien die Dateierweiterung .targets. TARGETS-Dateien werden meist am Ende zugeordneter Projektdateien importiert.

 Aufgabe

 Aufgaben sind Einheiten ausführbaren Codes, die in [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Projekten zum Ausführen von Buildvorgängen verwendet werden. Eine Aufgabe kann beispielsweise Eingabedateien kompilieren oder ein externes Tool ausführen. Weitere Informationen finden Sie unter [MSBuild-Aufgaben](../msbuild/msbuild-tasks.md).

 Transformieren

 Eine Transformation ist eine 1:1-Konvertierung von einer Elementauflistung in eine andere. Über Transformationen können nicht nur Elementauflistungen in einem Projekt transformiert werden, sondern auch direkte Zuordnungen zwischen Eingaben und Ausgaben eines Ziels identifiziert werden. Weitere Informationen finden Sie unter [Transforms](../msbuild/msbuild-transforms.md) (MSBuild-Transformationen).

 Bekannte Metadaten

 Siehe *Metadaten, bekannt*.

## <a name="see-also"></a>Siehe auch

- [MSBuild1](../msbuild/msbuild.md)