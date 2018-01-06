---
title: "Überschreiben und Erweitern der generierten Klassen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, providing overridable classes
ms.assetid: 30baa60d-a8ea-4611-96c1-8fcc3317cf21
caps.latest.revision: "15"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: d794edbb4f554e71e5d65a3e48e5393be61896a9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="overriding-and-extending-the-generated-classes"></a>Überschreiben und Erweitern der generierten Klassen
DSL-Definition ist eine Plattform, auf der Sie einen Satz leistungsstarken Tools erstellen können, die für eine domänenspezifische Sprache basieren. Viele Erweiterungen und Anpassung können vorgenommen werden, indem überschreiben und erweitern die Klassen, die aus der Definition der DSL generiert werden. Diese Klassen umfassen nicht nur die Domänenklassen, die Sie explizit in der DSL-Definitionsdiagramm definiert haben, sondern auch anderen Klassen, die Toolbox, -Explorer, Serialisierung und So weiter definieren.  
  
## <a name="extensibility-mechanisms"></a>Mechanismen für Erweiterbarkeit  
 Mehrere Mechanismen werden bereitgestellt, damit Sie den generierten Code erweitern können.  
  
### <a name="overriding-methods-in-a-partial-class"></a>Überschreiben von Methoden in einer partiellen Klasse  
 Partielle Klassendefinitionen ermöglichen eine Klasse in mehr als einem Ort definiert werden. Dadurch können Sie den generierten Code aus dem Code trennen, die Sie selbst schreiben. Im Code manuell geschrieben können Sie durch den generierten Code geerbte Klassen überschreiben.  
  
 Wenn in der Definition der DSL Sie eine Domänenklasse, die mit dem Namen definieren z. B. `Book`, benutzerdefinierten Code, der Methoden zum Überschreiben fügt geschrieben:  
  
 `public partial class Book`  
  
 `{`  
  
 `protected override void OnDeleting()`  
  
 `{`  
  
 `MessageBox.Show("Deleting book " + this.Title);`  
  
 `base.OnDeleting();`  
  
 `} }`  
  
> [!NOTE]
>  Um Methoden in einer generierten Klasse zu überschreiben, Schreiben Sie Code immer in einer Datei, die von die generierten Dateien getrennt ist. In der Regel wird die Datei in einem Ordner enthalten, mit dem Namen CustomCode. Wenn Sie Änderungen an den generierten Code vornehmen, gehen sie verloren, wenn Sie den Code aus der DSL-Definition neu generieren.  
  
 Geben Sie zum Ermitteln von welche Methoden Sie außer Kraft setzen können **überschreiben** in der Klasse, gefolgt von einem Leerzeichen. Die IntelliSense-QuickInfo informiert Sie, welche Methoden außer Kraft gesetzt werden können.  
  
### <a name="double-derived-classes"></a>Double-abgeleitete Klassen  
 Die meisten Methoden in der generierten Klassen werden vom einen festen Satz von Klassen in den Namespaces Modellierung geerbt. Allerdings werden einige Methoden in den generierten Code definiert. Normalerweise bedeutet dies, dass sie zu überschreiben; Sie können nicht in einer partiellen Klasse die Methoden überschreiben, die in einer anderen partiellen Definition der Klasse definiert sind.  
  
 Dennoch können Sie diese Methoden überschreiben, indem die **generiert doppelte abgeleitete** Flag für die Domänenklasse. Diese Ursachen zwei Klassen generiert werden, wird eine abstrakte Basisklasse des anderen. Alle Methoden- und Eigenschaftendefinitionen sind in der Basisklasse und nur der Konstruktor ist, in der abgeleiteten Klasse.  
  
 Im Beispiel Library.dsl, z. B. die `CirculationBook` Domänenklasse verfügt über die `Generates``Double Derived` -Eigenschaftensatz auf `true`. Der generierte Code für diese Domänenklasse enthält zwei Klassen:  
  
-   `CirculationBookBase`, dies ist eine abstrakte und alle Methoden und Eigenschaften enthält.  
  
-   `CirculationBook`, abgeleitet aus `CirculationBookBase`. Es ist leer, mit Ausnahme der Konstruktoren.  
  
 Um eine beliebige Methode zu überschreiben, Sie erstellen eine partielle Definition der abgeleiteten Klasse wie z. B. `CirculationBook`. Sie können die generierten Methoden und die vom Framework Modellierung geerbten Methoden überschreiben.  
  
 Sie können diese Methode mit allen Arten von Elementen, einschließlich der Modellelemente, Beziehungen, Formen, Diagrammen und Connectors verwenden. Sie können auch die Methoden anderer generierten Klassen überschreiben. Einige Klassen generiert, wie z. B. die ToolboxHelper immer Double-abgeleitet sind.  
  
### <a name="custom-constructors"></a>Benutzerdefinierte Konstruktoren  
 Einen Konstruktor kann nicht überschrieben werden. Der Konstruktor muss auch in Double abgeleitete Klassen in der abgeleiteten Klasse.  
  
 Wenn Sie einen eigene Konstruktor bereitstellen möchten, Sie können dazu `Has Custom Constructor` für die Domänenklasse in der DSL-Definition. Beim Klicken auf **alle Vorlagen transformieren**, der generierte Code enthält einen Konstruktor für diese Klasse nicht. Es wird ein Aufruf an den fehlenden Konstruktor enthalten. Dies bewirkt, dass einen Fehlerbericht, wenn Sie die Projektmappe zu erstellen. Doppelklicken Sie auf den Fehlerbericht an einen Kommentar in den generierten Code, der erklärt, was Sie bereitstellen sollten, finden Sie unter.  
  
 Schreiben Sie eine partielle Klassendefinition in einer Datei, die von die generierten Dateien getrennt ist, und geben Sie den Konstruktor.  
  
### <a name="flagged-extension-points"></a>Gekennzeichnete Erweiterungspunkte  
 Eine gekennzeichnete Erweiterungspunkt ist ein Ausgangspunkt in der DSL-Definition, in dem Sie festlegen können, eine Eigenschaft oder ein Kontrollkästchen, um anzugeben, dass Sie eine benutzerdefinierte Methode gewähren möchten. Benutzerdefinierte Konstruktoren sind ein Beispiel. Weitere Beispiele umfassen das Festlegen der `Kind` der Eigenschaft "Domain" berechnet oder benutzerdefinierten Speicher oder Einstellung der **ist Benutzerdefiniert** -Flag in einem verbindungsgenerator.  
  
 In jedem Fall Wenn Sie das Flag wird festgelegt, und generieren den Code verursacht einen Buildfehler. Doppelklicken Sie auf den Fehler, um einen Kommentar, der erläutert wird, müssen Sie angeben, finden Sie unter.  
  
### <a name="rules"></a>Regeln  
 Der Transaktions-Manager können Sie Regeln definieren, die vor dem Ende einer Transaktion ausgeführt werden, in dem ein angegebenen Ereignis, z. B. eine Änderung an einer Eigenschaft aufgetreten ist. Regeln werden in der Regel verwendet, um Synchronism zwischen verschiedenen Elementen im Speicher beizubehalten. Beispielsweise werden Regeln verwendet, um sicherzustellen, dass das Diagramm zeigt den aktuellen Zustand des Modells an.  
  
 Regeln werden auf Basis einer pro-Klasse definiert ist, so, dass Sie keinen Code haben registriert, die die Regel für jedes Objekt. Weitere Informationen finden Sie unter [weitergeben Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).  
  
### <a name="store-events"></a>Speichern von Ereignissen  
 Die Modellierung-Store bietet einen Ereignismechanismus, den Sie verwenden, um bestimmte Typen von Änderungen in den Speicher, einschließlich hinzufügen und Löschen von Elementen, die Änderungen von Eigenschaftswerten, überwachen und so weiter. Die Ereignishandler sind nach dem Schließen der Transaktion aufgerufen, in denen die Änderungen vorgenommen wurden. Diese Ereignisse werden in der Regel verwendet, auf Ressourcen außerhalb des Informationsspeichers aktualisiert.  
  
### <a name="net-events"></a>Ereignisse für .NET  
 Sie können einige Ereignisse Formen abonnieren. Sie können z. B. Mausklicks auf ein Shape lauscht. Sie müssen Code schreiben, der das Ereignis für jedes Objekt abonniert. Dieser Code kann in einer Überschreibung von InitializeInstanceResources() geschrieben werden.  
  
 Einige Ereignisse werden auf ShapeFields, generiert, die zum Zeichnen von Decorator-Elementen auf eine Form vom Typ verwendet werden. Ein Beispiel finden Sie unter [wie: Abfangen mit einem Klick auf eine Form oder einen Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).  
  
 Diese Ereignisse werden in der Regel nicht innerhalb einer Transaktion ausgeführt. Wenn Sie Änderungen im Speicher vornehmen möchten, sollten Sie eine Transaktion erstellen.