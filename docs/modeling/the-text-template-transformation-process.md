---
title: "The Text Template Transformation Process | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, transformation process"
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 30
---
# The Text Template Transformation Process
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Textvorlagen\-Transformationsprozess wird aus einer Textvorlagendatei \(Eingabe\) eine neue Textdatei \(Ausgabe\) generiert.  Textvorlagen können verwendet werden, um Visual Basic\- oder C\#\-Code oder einen HTML\-Bericht zu generieren.  
  
 Drei Komponenten sind an diesem Prozess beteiligt: das Modul, der Host und die Direktivenprozessoren.  Das Modul steuert den Prozess und interagiert mit dem Host und dem Direktivenprozessor, um die Ausgabedatei zu erzeugen.  Der Host übernimmt die Interaktion mit der Umgebung, z. B. die Suche nach Dateien und Assemblys.  Der Direktivenprozessor fügt Funktionen wie das Lesen von Daten aus einer XML\-Datei oder einer Datenbank hinzu.  
  
 Der Textvorlagen\-Transformationsprozess wird in zwei Schritten ausgeführt.  Zuerst erstellt das Modul eine als generierte Transformationsklasse bezeichnete temporäre Klasse.  Diese Klasse enthält den Code, der von den Direktiven und Kontrollblöcken generiert wird.  Danach wird die generierte Transformationsklasse vom Modul kompiliert und ausgeführt, um die Ausgabedatei zu erzeugen.  
  
## Komponenten  
  
|Komponente|Beschreibung|Vom Benutzer anpassbar \(Ja\/Nein\)|  
|----------------|------------------|-----------------------------------------|  
|Modul|Die Modulkomponente steuert den Textvorlagen\-Transformationsprozess.|Nein.|  
|Host|Der Host ist die Schnittstelle zwischen dem Modul und der Benutzerumgebung.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist ein Host des Texttransformationsprozesses.|Ja.  Sie können einen benutzerdefinierten Host schreiben.|  
|Direktivenprozessoren|Direktivenprozessoren sind Klassen, die Direktiven in Textvorlagen verarbeiten.  Mithilfe von Direktiven können Daten aus einer Eingabequelle für eine Textvorlage bereitgestellt werden.|Ja.  Sie können benutzerdefinierte Direktivenprozessoren schreiben.|  
  
## Modul  
 Das Modul empfängt die Vorlage in Form einer Zeichenfolge vom Host, der alle im Transformationsprozess verwendeten Dateien behandelt.  Das Modul weist den Host anschließend an, nach benutzerdefinierten Direktivenprozessoren und anderen Teilen der Umgebung zu suchen.  Danach wird die generierte Transformationsklasse vom Modul kompiliert und ausgeführt.  Das Modul gibt den generierten Text an den Host zurück, der den Text normalerweise in einer Datei speichert.  
  
## Host  
 Der Host ist für alle Vorgänge im Zusammenhang mit der Umgebung außerhalb des Transformationsprozesses zuständig, z. B.:  
  
-   Suchen nach Text\- und Binärdateien, die vom Modul oder einem Direktivenprozessor angefordert werden.  Der Host kann Verzeichnisse und den globalen Assemblycache nach Assemblys durchsuchen.  Der Host kann nach benutzerdefiniertem Direktivenprozessorcode für das Modul suchen.  Er kann auch Textdateien suchen und lesen und ihren Inhalt als Zeichenfolgen zurückgeben.  
  
-   Bereitstellen von Listen von Standardassemblys und \-namespaces, die vom Modul verwendet werden, um die generierte Transformationsklasse zu erstellen.  
  
-   Bereitstellen der Anwendungsdomäne, die verwendet wird, wenn die generierte Transformationsklasse vom Modul kompiliert und ausgeführt wird.  Es wird eine separate Anwendungsdomäne verwendet, um die Hostanwendung vor Fehlern im Vorlagencode zu schützen.  
  
-   Schreiben der generierten Ausgabedatei.  
  
-   Festlegen der Standarderweiterung für die generierte Ausgabedatei.  
  
-   Behandeln von Fehlern bei der Textvorlagentransformation.  Der Host kann die Fehler z. B. in der Benutzeroberfläche anzeigen oder in eine Datei schreiben.  \(In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] werden Fehler im Fehlermeldungsfenster angezeigt.\)  
  
-   Bereitstellen eines erforderlichen Parameterwerts, wenn ein Benutzer eine Direktive ohne Angabe eines Werts aufgerufen hat.  Der Direktivenprozessor kann den Namen der Direktive und den Parameter angeben und den Host anweisen, einen Standardwert bereitzustellen \(sofern verfügbar\).  
  
## Direktiven und Direktivenprozessoren  
 Eine Direktive ist ein Befehl in der Textvorlage.  Sie stellt Parameter für den Generierungsprozess bereit.  Normalerweise definieren Direktiven die Quelle und den Typ des Modells oder einer anderen Eingabe und die Dateinamenerweiterung der Ausgabedatei.  
  
 Ein Direktivenprozessor kann eine oder mehrere Direktiven verarbeiten.  Zum Transformieren einer Vorlage muss ein Direktivenprozessor installiert sein, der die Direktiven in der Vorlage verarbeiten kann.  
  
 Durch Direktiven wird Code in der generierten Transformationsklasse hinzugefügt.  Sie rufen Direktiven in einer Textvorlage auf, und das Modul verarbeitet alle Direktivenaufrufe beim Erstellen der generierten Transformationsklasse.  Nachdem Sie eine Direktive erfolgreich aufgerufen haben, kann der restliche Code, den Sie in der Textvorlage schreiben, auf der von der Direktive bereitgestellten Funktion beruhen.  Sie können in der Vorlage z. B. den folgenden Aufruf der `import`\-Direktive ausführen:  
  
 `<#@ import namespace="System.Text" #>`  
  
 Der Standarddirektivenprozessor konvertiert dies in der generierten Transformationsklasse in eine `using`\-Anweisung.  Im Rest des Vorlagencodes kann die `StringBuilder`\-Klasse dann verwendet werden, ohne sie als `System.Text.StringBuilder` zu qualifizieren.