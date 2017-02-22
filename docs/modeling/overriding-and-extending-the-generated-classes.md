---
title: "&#220;berschreiben und Erweitern der generierten Klassen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Bereitstellen von überschreibbaren Klassen"
ms.assetid: 30baa60d-a8ea-4611-96c1-8fcc3317cf21
caps.latest.revision: 15
caps.handback.revision: 15
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# &#220;berschreiben und Erweitern der generierten Klassen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die DSL\-Definition ist eine Plattform, auf der Sie einen Satz leistungsstarker Tools erstellen können, die auf eine domänenspezifische Sprache sind.  Viele Erweiterungen und Anpassungen können vorgenommen werden, indem Sie die Klassen überschrieben und erweitert, die von der DSL\-Definition generiert werden.  Diese Klassen umfassen nicht nur die Domänen Klassen, die Sie explizit DSL\-Definitions im Diagramm definiert haben, sondern auch weitere Klassen, die die Toolbox Serialisierung Projektmappen\-Explorer definieren, usw.  
  
## Erweiterbarkeits\-Mechanismen  
 Einige Mechanismen werden bereitgestellt, um es Ihnen zu ermöglichen, den generierten Code zu erweitern.  
  
### Überschreiben von Methoden in einer partiellen Klasse  
 Partielle Klassendefinitionen ermöglichen eine in mehr als einem Ort Klasse definiert sein.  Dies ermöglicht es Ihnen, den generierten Code von Code zu trennen, den Sie selbst schreiben.  Im manuell\-geschriebenen Code können Sie die Klassen überschreiben, die vom generierten Code geerbt werden.  
  
 Wenn z. B. in der DSL\-Definition Sie eine Domänenklasse definieren, die `Book`genannt wird, können Sie benutzerdefinierten Code schreiben, der Überschreibungsmethoden hinzugefügt wird:  
  
 `public partial class Book`  
  
 `{`  
  
 `protected override void OnDeleting()`  
  
 `{`  
  
 `MessageBox.Show("Deleting book " + this.Title);`  
  
 `base.OnDeleting();`  
  
 `} }`  
  
> [!NOTE]
>  Um Methoden in einer generierten Klasse zu überschreiben, schreiben Sie immer den Code in einer Datei, die von den generierten Dateien aufgeteilt ist.  In der Regel wird die Datei in einem Ordner enthalten, der CustomCode benannt ist.  Wenn Sie Änderungen am generierten Code vornehmen, sind sie verloren, wenn Sie den Code aus der DSL\-Definition erneut generieren.  
  
 Um zu ermitteln, welche Methoden überschreiben Sie in der Überschreibung Typ, gefolgt von einem Leerzeichen Klasse.  Die IntelliSense\-QuickInfo teilt Ihnen mit, welche Methoden überschrieben werden können.  
  
### DOUBLE\-Abgeleitete Klassen  
 Die meisten Methoden in generierten Klassen werden von einem festen Satz von Klassen in den Namespaces Modellierungs geerbt.  Allerdings sind einige Methoden im generierten Code definiert.  Normalerweise bedeutet dies, dass Sie sie nicht überschrieben werden kann. Sie können nicht in einer partiellen Klasse die Methoden überschreiben, die in einer anderen partiellen Definition der gleichen Klasse definiert sind.  
  
 Trotzdem können Sie diese Methoden überschreiben, indem Sie das **Generiert abgeleitetes Double**\-Flag für die Domänenklasse festlegen.  Dies bewirkt, dass zwei Klassen generiert werden sollen, eine abstrakte Basisklasse, die eine der anderen ist.  Alle Methoden\- und Eigenschaftendefinitionen sind in der Basisklasse, und nur der Konstruktor ist in der abgeleiteten Klasse.  
  
 Beispielsweise wird im Beispiel Library.dsl, hat die `CirculationBook` Domänenklasse den `Generates`Eigenschaft`Double Derived` zu `true`.  Der generierte Code für diese Domänenklasse enthält zwei Klassen:  
  
-   `CirculationBookBase`, das eine Zusammenfassung und das alle Methoden und Eigenschaften enthält.  
  
-   `CirculationBook`, das von `CirculationBookBase`abgeleitet ist.  Sie sind, außer den Konstruktoren leer.  
  
 Für jede Methode zu überschreiben, erstellen Sie eine partielle Definition der abgeleiteten Klasse, wie `CirculationBook`.  Sie können die generierten Methoden und Methoden überschreiben, die vom Modellierungs Framework vererbt werden.  
  
 Sie können diese Methode mit allen Typen von Modellelementen, einschließlich Element, Beziehungen, Formen und Konnektoren, Diagramme verwenden.  Sie können Methoden anderer generierte Klassen überschreiben.  Einige generierte Klassen, z. B. das ToolboxHelper sind immer DOUBLE\-abgeleitet.  
  
### Benutzerdefinierte Konstruktoren  
 Sie können keinen Konstruktor überschreiben.  Sogar in den DOUBLE\-abgeleiteten Klassen, muss der Konstruktor der abgeleiteten Klasse sein.  
  
 Wenn Sie bereitstellen möchten, Konstruktor verfügen, können Sie dazu `Has Custom Constructor` für die Domänenklasse in der DSL\-Definition festlegen.  Wenn Sie auf **Alle Vorlagen transformieren**klicken, enthält der generierte Code keinen Konstruktor für diese Klasse.  Es enthält einen Aufruf an den fehlenden Konstruktor ein.  Dies verursacht einen Fehlerbericht, wenn Sie die Projektmappe erstellen.  Doppelklicken Sie auf den Fehlerbericht, um einen Kommentar im generierten Code zu sehen, der erklärt, wie Sie bereitstellen möchten.  
  
 Schreiben Sie eine partielle Klassendefinition in der Datei getrennt von den generierten Dateien lautet, und stellen Sie den Konstruktor bereit.  
  
### Gekennzeichnete Erweiterungs\-Punkte  
 Ein gekennzeichneter ist ein Erweiterungspunkt DSL\-Definition in der Stelle, an der Sie eine Eigenschaft oder ein Kontrollkästchen festlegen können, um anzugeben, dass Sie eine benutzerdefinierte Methode bereitstellen.  Benutzerdefinierte Konstruktoren sind ein Beispiel.  Andere Beispiele hierfür sind das Festlegen `Kind` einer Domäneneigenschaft dem berechneten oder benutzerdefinierten Speicher oder Festlegen des **Ist benutzerdefiniert**\-Flags in einem Generator Verbindungen.  
  
 In jedem Fall wenn erneut generieren Sie legen das Flag und den Code ein Buildfehler auftreten.  Doppelklicken Sie auf den Fehler, um einen Kommentar anzeigen, der erklärt, wie Sie bereitstellen müssen.  
  
### Regeln  
 Der Transaktions\-Manager können Sie Regeln zu definieren, die vor dem Ende einer Transaktion, in der ein Menge Ereignis aufgetreten ist, z. B. eine Änderung an einer Eigenschaft ausgeführt werden.  Die Regeln werden in der Regel Synchronismus zwischen verschiedenen Elementen im Speicher beizubehalten.  Beispielsweise werden Regeln, um zu überprüfen, ob das Diagramm den aktuellen Zustand des Modells angezeigt wird.  
  
 Regeln werden auf Basis einer einzelnen Klasse definiert, sodass Sie Code nicht benötigen, der die Regel für jedes Objekt registriert.  Weitere Informationen finden Sie unter [Regeln propagieren Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).  
  
### Speichern von Ereignissen  
 Der Modellierungs Datenspeicher stellt einen Ereignismechanismus, den Sie verwenden können, um bestimmte Typen von Änderungen im Speicher, einschließlich Hinzufügen und Löschen von Elementen zu überwachen, Änderungen an Eigenschaftswerten usw.  Die Ereignishandler werden aufgerufen, nachdem der Abschluss der Transaktion, in der die Änderungen vorgenommen wurden.  Normalerweise werden diese Ereignisse verwendet werden, um Ressourcen außerhalb des Arbeitsspeichers zu aktualisieren.  
  
### .NET\-Ereignisse  
 Sie können in einigen Ereignissen auf Forms abonnieren.  Sie können z. B. auf Mausklicks auf einem Formular überwachen.  Sie müssen Code schreiben, der an das Ereignis für jedes Objekt abonniert.  Dieser Code kann in eine Überschreibung von InitializeInstanceResources\(\) geschrieben werden.  
  
 Einige Ereignisse werden in ShapeFields generiert, die verwendet werden, um Decorator\-Elemente auf einem Formular zu zeichnen.  Ein entsprechendes Beispiel finden Sie unter [Gewusst wie: Abfangen eines Klicks auf eine Form oder einen Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).  
  
 Diese Ereignisse treten normalerweise nicht innerhalb einer Transaktion ausgeführt wurde.  Sie sollten eine Transaktion erstellen, wenn Sie Änderungen im Speicher vornehmen möchten.