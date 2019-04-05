---
title: Das Textvorlagen-Transformationsprozess | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cf7f84d8900443d6fec9b84995c569ef21ed0e86
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961309"
---
# <a name="the-text-template-transformation-process"></a>Textvorlagen-Transformationsprozess
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Textvorlagen-Transformationsprozess akzeptiert eine Textvorlagendatei als Eingabe und eine neue Textdatei als Ausgabe generiert. Beispielsweise können Sie Textvorlagen um Visual Basic- oder C#-Code zu generieren, oder Sie können einen HTML-Bericht generieren.  
  
 Drei Komponenten nehmen Sie Teil, in diesem Prozess: das Modul, dem Host und anweisungsprozessoren. Die Engine steuert, den Prozess; er interagiert mit dem Host und der anweisungsprozessor aus, um die Ausgabedatei zu erstellen. Vom Host bereitgestellten jegliche Interaktion mit der Umgebung, z. B. die Suche von Dateien und Assemblys. Der anweisungsprozessor fügt Funktionen, wie z. B. das Lesen von Daten aus einer XML-Datei oder eine Datenbank hinzu.  
  
 Das Textvorlagen-Transformationsprozess wird in zwei Schritten ausgeführt. Die Engine erstellt zunächst eine temporäre Klasse, die generierten Transformationsklasse genannt wird. Diese Klasse enthält den Code, der von der-Direktiven und Kontrollblöcke generiert wird. Danach wird das Modul kompiliert und führt die generierten Transformationsklasse, um die Ausgabedatei zu erstellen.  
  
## <a name="components"></a>Komponenten  
  
|Komponente|Beschreibung|Anpassbare (Ja/Nein)|  
|---------------|-----------------|------------------------------|  
|Engine|Die Engine-Komponente steuert das Textvorlagen-Transformationsprozess|Nein.|  
|Host|Der Host ist die Schnittstelle zwischen der Engine und der benutzerumgebung. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ist ein Host des Texttransformationsprozesses.|Ja. Sie können einen benutzerdefinierten Host schreiben.|  
|Direktivenprozessoren|Direktivenprozessoren sind Klassen, die Anweisungen in den Textvorlagen zu verarbeiten. Anweisungen können Sie Daten aus der Eingabequelle eine Textvorlage bereitstellt.|Ja. Sie können benutzerdefinierte anweisungsprozessoren schreiben.|  
  
## <a name="the-engine"></a>Die Engine  
 Das Modul empfängt die Vorlage als eine Zeichenfolge mit dem Host, der alle Dateien verarbeitet, die im Transformationsprozess verwendet werden. Das Modul fragt dann den Host aus, um eine beliebige benutzerdefinierten anweisungsprozessoren und andere Aspekte der Umgebung zu suchen. Die Engine wird dann kompiliert und führt die generierten Transformationsklasse. Das Modul gibt den generierten Text zurück, an den Host, der normalerweise den Text einer Datei speichert.  
  
## <a name="the-host"></a>Hosting  
 Der Host ist verantwortlich für alle Elemente, die mit der Umgebung außerhalb des Transformationsvorgangs, einschließlich der folgenden verknüpft:  
  
-   Suchen von Text und Binärdateien, die von der Engine oder ein anweisungsprozessor angefordert. Der Host kann es sich um Verzeichnisse und den globalen Assemblycache nach Assemblys durchsuchen. Der Host kann benutzerdefinierten anweisungsprozessor-Code für das Modul suchen. Der Host kann auch suchen und Lesen von Textdateien und ihren Inhalt als Zeichenfolgen zurückgegeben.  
  
-   Bereitstellen von Listen mit standard-Assemblys und Namespaces, die von der Engine verwendet werden, um die generierten Transformationsklasse zu erstellen.  
  
-   Bereitstellen der Anwendungsdomäne, die verwendet wird, wenn das Modul kompiliert und führt die generierten Transformationsklasse. Eine separate Anwendungsdomäne wird verwendet, um die hostanwendung von Fehlern im Vorlagencode zu schützen.  
  
-   Schreiben die generierte Ausgabedatei an.  
  
-   Wenn die standarderweiterung für die generierte Ausgabedatei an.  
  
-   Behandeln von Fehlern bei der Textvorlagentransformation. Beispielsweise kann der Host die Fehler in der Benutzeroberfläche anzeigen oder in eine Datei schreiben. (In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Fehler im Fenster mit Fehlermeldungen angezeigt.)  
  
-   Einen Erforderlicher Parameterwert bereit, wenn ein Benutzer eine Richtlinie aufgerufen hat, ohne einen Wert. Der anweisungsprozessor kann Geben Sie den Namen der Anweisung und der Parameter, und bitten Sie den Host auf einen Standardwert angeben, sofern vorhanden.  
  
## <a name="directives-and-directive-processors"></a>Anweisungen und Anweisungsprozessoren  
 Eine Direktive ist ein Befehl in der Textvorlage. Es stellt Parameter für den Generierungsprozess bereit. In der Regel definieren Direktiven, die Quelle und Typ des Modells oder andere Eingabe und die Dateinamenerweiterung der Ausgabedatei.  
  
 Ein anweisungsprozessor kann eine oder mehrere Anweisungen verarbeitet werden. Beim Transformieren einer Vorlage muss einen anweisungsprozessor installiert haben, der die Anweisungen in der Vorlage behandeln können.  
  
 Hinzufügen von Code in der generierten Transformationsklasse funktionieren Anweisungen. Rufen Sie Anweisungen von einer Textvorlage, und das Modul verarbeitet alle-Direktive Aufrufe, bei der Erstellung der generierten Transformationsklasse. Nachdem Sie eine Richtlinie erfolgreich aufzurufen, kann der Rest des Codes, den Sie in der Textvorlage schreiben auf die Funktionen verlassen, von der Anweisung bereitgestellten. Sie können z. B. den folgenden Aufruf machen die `import` -Direktive in der Vorlage:  
  
 `<#@ import namespace="System.Text" #>`  
  
 Der standard anweisungsprozessor konvertiert diese Option, um eine `using` -Anweisung in der generierten Transformationsklasse. Anschließend können Sie die `StringBuilder` Klasse in der restlichen Vorlagencode ohne Qualifizierung als `System.Text.StringBuilder`.
