---
title: Der Text Vorlagen-Transformationsprozess | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7322724b2118cb8b844262696a6e7cbd91a74e9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658504"
---
# <a name="the-text-template-transformation-process"></a>Textvorlagen-Transformationsprozess
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Textvorlagen-Transformationsprozess nimmt eine Textvorlagen Datei als Eingabe an und generiert eine neue Textdatei als Ausgabe. Beispielsweise können Sie Textvorlagen verwenden, um Visual Basic oder C# Code zu generieren, oder Sie können einen HTML-Bericht generieren.

 An diesem Prozess sind drei Komponenten beteiligt: die Engine, der Host und die direktivenprozessoren. Die Engine steuert den Prozess. Er interagiert mit dem Host und dem Direktivenprozessor, um die Ausgabedatei zu entwickeln. Der Host bietet eine beliebige Interaktion mit der Umgebung, z. b. das Suchen von Dateien und Assemblys. Der Anweisungs Prozessor fügt Funktionen hinzu, z. b. das Lesen von Daten aus einer XML-Datei oder einer Datenbank.

 Der Textvorlagen-Transformationsprozess wird in zwei Schritten ausgeführt. Zuerst erstellt die Engine eine temporäre Klasse, die als generierte Transformations Klasse bezeichnet wird. Diese Klasse enthält den Code, der von den Direktiven und Kontroll Blöcken generiert wird. Danach kompiliert die Engine die generierte Transformations Klasse und führt Sie aus, um die Ausgabedatei zu erstellen.

## <a name="components"></a>Komponenten

|Komponente|Beschreibung|Anpassbar (Ja/Nein)|
|---------------|-----------------|------------------------------|
|Ge|Die Engine-Komponente steuert den Textvorlagen-Transformationsprozess|Nein.|
|Host|Der Host ist die Schnittstelle zwischen der-Engine und der Benutzerumgebung. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ist ein Host des Text Transformationsprozesses.|Ja. Sie können einen benutzerdefinierten Host schreiben.|
|Direktivenprozessoren|Direktivenprozessoren sind Klassen, die Direktiven in Textvorlagen verarbeiten. Sie können-Direktiven verwenden, um Daten für eine Textvorlage aus einer Eingabe Quelle bereitzustellen.|Ja. Sie können benutzerdefinierte direktivenprozessoren schreiben.|

## <a name="the-engine"></a>Die Engine
 Die Engine empfängt die Vorlage als Zeichenfolge vom Host, der alle Dateien verarbeitet, die im Transformationsprozess verwendet werden. Die Engine fordert dann den Host auf, beliebige benutzerdefinierte direktivenprozessoren und andere Aspekte der Umgebung zu finden. Die Engine kompiliert dann die generierte Transformations Klasse und führt Sie aus. Die Engine gibt den generierten Text an den Host zurück, der normalerweise den Text in einer Datei speichert.

## <a name="the-host"></a>Hosting
 Der Host ist verantwortlich für alle Elemente, die sich außerhalb des Transformationsprozesses auf die Umgebung beziehen, einschließlich der folgenden:

- Suchen von Text-und Binärdateien, die vom Modul oder einem Direktivenprozessor angefordert werden. Der Host kann Verzeichnisse und den globalen Assemblycache suchen, um Assemblys zu suchen. Der Host kann benutzerdefinierten direktivenprozessorcode für die Engine finden. Der Host kann auch Textdateien suchen und lesen und ihren Inhalt als Zeichen folgen zurückgeben.

- Bereitstellen von Listen mit Standardassemblys und Namespaces, die von der-Engine zum Erstellen der generierten Transformations Klasse verwendet werden.

- Bereitstellen der Anwendungsdomäne, die verwendet wird, wenn die Engine die generierte Transformations Klasse kompiliert und ausführt. Eine separate Anwendungsdomäne wird verwendet, um die Host Anwendung vor Fehlern im Vorlagen Code zu schützen.

- Die generierte Ausgabedatei wird geschrieben.

- Die Standard Erweiterung für die generierte Ausgabedatei wird festgelegt.

- Behandeln von Fehlern bei der Textvorlagen Transformation. Der Host kann z. b. die Fehler in der Benutzeroberfläche anzeigen oder Sie in eine Datei schreiben. (In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] werden Fehler im Fenster Fehlermeldung angezeigt.)

- Bereitstellen eines erforderlichen Parameter Werts, wenn ein Benutzer eine-Direktive aufgerufen hat, ohne einen Wert bereitzustellen. Der Direktivenprozessor kann den Namen der Direktive und den-Parameter angeben und den Host auffordern, einen Standardwert anzugeben, wenn er über einen Wert verfügt.

## <a name="directives-and-directive-processors"></a>Direktiven und direktivenprozessoren
 Eine-Direktive ist ein Befehl in der Textvorlage. Sie stellt Parameter für den Generierungsprozess bereit. In der Regel definieren-Direktiven die Quelle und den Typ des Modells oder einer anderen Eingabe und die Dateinamenerweiterung der Ausgabedatei.

 Ein Direktivenprozessor kann eine oder mehrere Direktiven verarbeiten. Wenn Sie eine Vorlage transformieren, müssen Sie einen Direktivenprozessor installiert haben, der die Anweisungen in der Vorlage behandeln kann.

 Direktiven funktionieren, indem Sie Code in der generierten Transformations Klasse hinzufügen. Sie rufen Direktiven aus einer Textvorlage auf, und die Engine verarbeitet alle direktivenaufrufe, wenn die generierte Transformations Klasse erstellt wird. Nachdem Sie eine-Direktive erfolgreich aufgerufen haben, kann der Rest des Codes, den Sie in der Textvorlage schreiben, von der Funktionalität abhängen, die die-Direktive bereitstellt. Beispielsweise können Sie den folgenden Befehl für die `import`-Direktive in ihrer Vorlage durchführen:

 `<#@ import namespace="System.Text" #>`

 Der Standard Direktivenprozessor konvertiert diesen in eine `using`-Anweisung in der generierten Transformations Klasse. Anschließend können Sie die `StringBuilder`-Klasse im restlichen Vorlagen Code verwenden, ohne Sie als `System.Text.StringBuilder` zu qualifizieren.
