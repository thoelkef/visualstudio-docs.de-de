---
title: Inkrementelle Builds | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, incremental builds
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 17f33be85a5baf35235721c720386dd237d9ec85
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
ms.locfileid: "31572975"
---
# <a name="incremental-builds"></a>Inkrementelle Builds
Inkrementelle Builds sind Buildvorgänge, die so optimiert werden, dass Ziele mit Ausgabedateien, die hinsichtlich der zugehörigen Eingabedateien aktuell sind, nicht ausgeführt werden. Zielelemente können über ein `Inputs`-Attribut, das die Elemente angibt, die das Ziel als Eingabe erwartet, sowie ein `Outputs`-Attribut verfügen, das die Elemente angibt, die es als Ausgabe erzeugt. MSBuild versucht, zwischen den Werten dieser Attribute eine 1:1-Zuordnung zu erzielen. Wenn eine 1:1-Zuordnung vorhanden ist, vergleicht MSBuild den Zeitstempel jedes Eingabeelements mit dem Zeitstempel des zugehörigen Ausgabeelements. Ausgabedateien ohne 1:1-Zuordnung werden mit allen Eingabedateien verglichen. Ein Element wird als aktuell betrachtet, wenn dessen Ausgabedatei genau so alt oder neuer als seine Eingabedatei oder -dateien ist.  
  
 Wenn alle Ausgabeelemente aktuell sind, überspringt MSBuild das Ziel. Mit diesem *inkrementellen Build* kann die Buildgeschwindigkeit für das Ziel entscheidend erhöht werden. Wenn nur einige Dateien aktuell sind, führt MSBuild das Ziel aus, überspringt jedoch die aktuellen Elemente und bringt so alle Elemente auf den aktuellen Stand. Dies wird als *partieller inkrementeller Build* bezeichnet.  
  
 1:1-Zuordnungen werden in der Regel durch Elementtransformationen erzeugt. Weitere Informationen finden Sie unter [Transformationen](../msbuild/msbuild-transforms.md).  
  
 Betrachten Sie das folgende Ziel.  
  
```xml  
<Target Name="Backup" Inputs="@(Compile)"   
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">  
    <Copy SourceFiles="@(Compile)" DestinationFiles=  
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />  
</Target>  
```  
  
 Der durch den `Compile`-Elementtyp dargestellte Satz von Dateien wird in ein Sicherungsverzeichnis kopiert. Die Sicherungsdateien weisen die Dateinamenerweiterung .bak auf. Wenn die durch den `Compile`-Elementtyp dargestellten Dateien oder die entsprechenden Sicherungsdateien nach dem Ausführen des Sicherungsziels nicht gelöscht oder geändert werden, wird das Sicherungsziel in nachfolgenden Builds übersprungen.  
  
## <a name="output-inference"></a>Ausgaberückschluss  
 MSBuild bestimmt durch Vergleich des `Inputs`-Attributs mit dem `Outputs`-Attribut eines Ziels, ob dieses ausgeführt werden muss. Idealerweise bleibt der nach einem inkrementellen Build vorhandene Satz von Dateien unabhängig davon gleich, ob die zugeordneten Ziele ausgeführt werden oder nicht. Da sich Eigenschaften und Elemente, die von Aufgaben erstellt oder geändert werden, auf den Build auswirken können, muss MSBuild deren Werte auch dann ableiten, wenn das Ziel, das sich auf sie auswirkt, übersprungen wird. Dies wird als *Ausgaberückschluss* bezeichnet.  
  
 Drei Fälle werden unterschieden:  
  
-   Das Ziel weist ein `Condition`-Attribut auf, das zu `false` ausgewertet wird. In diesem Fall wird das Ziel nicht ausgeführt, und hat keine Auswirkungen auf den Build.  
  
-   Das Ziel weist veraltete Ausgaben auf und wird ausgeführt, um diese auf den aktuellen Stand zu bringen.  
  
-   Das Ziel weist keine veralteten Ausgaben auf und wird übersprungen. MSBuild wertet das Ziel aus und nimmt Änderungen an Elementen und Eigenschaften vor, als ob das Ziel ausgeführt worden wäre.  
  
 Zur Unterstützung der inkrementellen Kompilierung müssen Aufgaben sicherstellen, dass der `TaskParameter`-Attributwert jedes `Output`-Elements gleich einem Aufgabeneingabeparameter ist. Hier einige Beispiele:  
  
```xml  
<CreateProperty Value="123">  
    <Output PropertyName="Easy" TaskParameter="Value" />  
</CreateProperty>  
```  
  
 Damit wird die Easy-Eigenschaft mit dem Wert "123" erstellt, unabhängig davon, ob das Ziel ausgeführt oder übersprungen wird.  
  
```xml  
<CreateItem Include="a.cs;b.cs">  
    <Output ItemName="Simple" TaskParameter="Include" />  
</CreateItem>  
```  
  
 Damit wird der Simple-Elementtyp mit den beiden Elementen, "a.cs" und "b.cs" erstellt, unabhängig davon, ob das Ziel ausgeführt oder übersprungen wird.  
  
 Ab MSBuild 3.5 wird der Ausgaberückschluss automatisch für Element- und Eigenschaftengruppen in einem Ziel ausgeführt. `CreateItem`-Aufgaben sind in einem Ziel nicht erforderlich und sollten vermieden werden. Zudem sollten `CreateProperty`-Aufgaben in einem Ziel nur verwendet werden, um zu bestimmen, ob dieses ausgeführt wurde.  
  
## <a name="determining-whether-a-target-has-been-run"></a>Bestimmen, ob ein Ziel ausgeführt wurde  
 Aufgrund des Ausgaberückschlusses müssen Sie einem Ziel eine `CreateProperty`-Aufgabe hinzufügen, um Eigenschaften und Elemente untersuchen und so bestimmen zu können, ob das Ziel ausgeführt wurde. Fügen Sie dem Ziel die Aufgabe `CreateProperty` hinzu, und weisen Sie dieser ein `Output`-Element zu, dessen `TaskParameter` auf "ValueSetByTask" festgelegt ist.  
  
```xml  
<CreateProperty Value="true">  
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />  
</CreateProperty>  
```  
  
 Damit wird, sofern das Ziel ausgeführt wird, die CompileRan-Eigenschaft mit dem Wert `true` erstellt. Wenn das Ziel übersprungen wird, wird CompileRan nicht erstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Ziele](../msbuild/msbuild-targets.md)