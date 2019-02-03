---
title: Analysieren von Code Coverage in Buildüberprüfungstests | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 59c07d15-511e-4fd0-b398-bde9d5ed00d9
caps.latest.revision: 10
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e7525fe8e01922880199275576a8b12ec29bc029
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834932"
---
# <a name="analyzing-code-coverage-in-build-verification-tests"></a>Analysieren von Code Coverage in Buildüberprüfungstests
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Code Coverage-Analyse in Microsoft Visual Studio zeigt Ihnen, wie viel Ihres Codes durch automatische Test untersucht wird. Weitere Informationen finden Sie unter [Using Code Coverage to Determine How Much Code is being Tested (Wie Sie feststellen können, wie viel Code untersucht wird)](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 Wenn Sie Code einchecken, werden Ihre Tests zusammen mit allen anderen Tests von anderen Teammitgliedern auf dem Buildserver ausgeführt. (Wenn Sie dies noch nicht eingerichtet haben, finden Sie unter [Ausführen von Tests im Buildprozess](http://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38) Informationen hierzu.) Es ist hilfreich, die Code Coverage für den Builddienst zu analysieren, da Sie dadurch das aktuellste und umfassendste Bild der Code Coverage für das gesamte Projekt erhalten. Dazu gehören auch automatisierte Systemtests und andere codierte Tests, die Sie normalerweise nicht auf Entwicklungscomputern ausführen.  
  
1. Öffnen Sie im Team Explorer **Builds**, und fügen Sie dann eine Builddefinition hinzu oder bearbeiten Sie diese.  
  
2. Erweitern Sie auf der Seite **Prozess** die Elemente **Automatisierte Tests**, **Testquelle** und **Testlaufeinstellungen**. Legen Sie die Option **Code Coverage Enabled**(Code Coverage aktiviert) für den **Type of Run Settings File**(Typ der Laufzeiteinstellungsdatei) fest.  
  
    Wenn Sie über mehrere Testquelldefinitionen verfügen, wiederholen Sie diesen Schritt für jede einzelne Definition.  
  
   - <em>Es ist jedoch kein Feld mit dem Namen *Type of Run Settings File</em> (Typ der Laufzeiteinstellungsdatei) vorhanden.*  
  
      Wählen Sie **Testassembly** unter **Automatisierte Tests**, und klicken Sie auf die Schaltfläche mit den Auslassungspunkten **[...]** am Ende der Zeile. Wählen Sie unter **Test Runner** im Dialogfeld **Testlauf hinzufügen/bearbeiten** die Option **Visual Studio Test Runner** aus.  
  
   ![Festlegen der Builddefinition für Code Coverage](../test/media/codecoverage-plaincc.png "CodeCoverage-plainCC")  
  
   Nach Ausführung des Builds werden die Code Coverage-Ergebnisse in der Buildzusammenfassung angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
