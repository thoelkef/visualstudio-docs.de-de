---
title: "Gewusst wie: Definieren von Schl&#252;sselw&#246;rtern in Visual&#160;C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Benutzerschlüsselwörter"
  - "Reservierte Wörter, benutzerdefinierte Schlüsselwörter"
  - "Benutzerdefinierte Schlüsselwörter"
  - "Reservierte Schlüsselwörter, benutzerdefiniert"
  - "usertype.dat"
  - "Schlüsselwörter [C++], benutzerdefiniert"
ms.assetid: 2dfcf343-e861-4bde-b5a4-7deb6773d9c8
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Gewusst wie: Definieren von Schl&#252;sselw&#246;rtern in Visual&#160;C++
Schlüsselwörter sind vordefinierte, reservierte Bezeichner, die besondere Bedeutungen haben. Sie können in einem Programm nicht als Bezeichner verwendet werden. Allerdings können Sie eigene Schlüsselwörter für die Verwendung in Visual C\+\+ definieren, und können Sie den Schlüsselwörtern eine benutzerdefinierte Syntaxfarbe zuweisen. Durch die syntaxbezogene Farbzuweisung erhalten Sie optische Hinweise zur Struktur und zum Zustand des Codes.  
  
### So definieren Sie eigene Visual C\+\+\-Schlüsselwörter  
  
1.  Verwenden Sie den [Code\- und Text\-Editor](http://msdn.microsoft.com/de-de/508e1f18-99d5-48ad-b5ad-d011b21c6ab1) von Visual Studio oder „Notepad.exe“, um eine Nur\-Text\-Datei namens `usertype.dat` zu erstellen.  
  
2.  Geben Sie in `usertype.dat` jedes benutzerdefinierte Schlüsselwort in einer separaten Zeile ein.  
  
3.  Speichern Sie `usertype.dat` in dem Verzeichnis, das die Datei „devenv.exe“ enthält. Standardmäßig ist der Pfad dieses Verzeichnisses *\<Laufwerk\>*:\\Programme\\[!INCLUDE[TLA#tla_visualstu](../misc/includes/tlasharptla_visualstu_md.md)] *\<Hauptversion.Nebenversionnummer\>*\\Common7\\[!INCLUDE[TLA2#tla_ide](../misc/includes/tla2sharptla_ide_md.md)]. Da dieses Verzeichnis standardmäßig schreibgeschützt ist, benötigen Sie Administratoranmeldeinformationen, um `usertype.dat` zu speichern.  
  
4.  Beenden Sie Visual Studio, und starten Sie es anschließend neu.  
  
    > [!NOTE]
    >  Sie können die Datei `usertype.dat` während einer Bearbeitungssitzung weder umbenennen noch neu laden, da sie während der Initialisierung gelesen wird. Alle zuvor definierten Farbeinstellungen haben Vorrang, da der Mechanismus für die Syntaxfarben die Datei `usertype.dat` zuletzt überprüft.  
  
5.  Klicken Sie im Menü **Extras** auf **Optionen**. Klicken Sie im Dialogfeld **Optionen** auf **Umgebung**, dann auf **Schriftarten und Farben**, und klicken Sie anschließend in der Liste **Elemente anzeigen:** auf **C\/C\+\+\-Benutzerschlüsselwörter**.  
  
6.  Legen Sie die Eigenschaften für Schriftart und Farbe für Ihre benutzerdefinierten Schlüsselwörter gemäß der Beschreibung in [Schriftarten und Farben, Umgebung, Dialogfeld "Optionen"](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) fest.  
  
 Weitere Informationen finden Sie unter [C\+\+\-Schlüsselwörter](/visual-cpp/cpp/keywords-cpp).  
  
## Siehe auch  
 [Ausführen als Mitglied der Gruppe Benutzer](/visual-cpp/top/running-as-a-member-of-the-users-group)   
 [Standardtastenkombinationen](../ide/default-keyboard-shortcuts-in-visual-studio.md)