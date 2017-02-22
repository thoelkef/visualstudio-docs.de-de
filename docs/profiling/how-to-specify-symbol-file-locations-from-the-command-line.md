---
title: "Gewusst wie: Angeben von Symboldateispeicherorten &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Angeben von Symboldateispeicherorten &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um Symbolinformationen, wie z. B. Funktionsnamen und Zeilennummern, anzuzeigen, benötigt das VSPerfReport\-Befehlszeilentool Zugriff auf die Symboldateien \(.pdb\) der profilierten Komponenten und auf die Windows\-Systemdateien.  Symboldateien werden erstellt, wenn eine Komponente kompiliert wird.  Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  VSPerfReport sucht automatisch in den folgenden Speicherorten nach Symboldateien:  
  
-   In der **\/SymbolPath**\-Option oder in der **\_NT\_SYMBOL\_PATH**\-Option angegebene Pfade  
  
-   Der genaue lokale Pfad, in dem eine Komponente kompiliert wurde  
  
-   Das Verzeichnis mit der Profilerstellungs\-Datendatei \(.vsp oder .vsps\)  
  
 Microsoft stellt die PDB\-Dateien für viele seiner Produkte online auf einem Symbolserver bereit.  Wenn der Computer, den Sie zur Berichterstellung verwenden, über eine Verbindung zum Internet verfügt, stellt VSPerfReport eine Verbindung mit dem Onlinesymbolserver her, um automatisch nach Symbolinformationen zu suchen und die Dateien in einem lokalen Speicher zu speichern.  
  
 Sie können den Speicherort von Symboldateien und den Speicher des Microsoft\-Symbolservers folgendermaßen angeben:  
  
-   Legen Sie die **\_NT\_SYMBOL\_PATH**\-Umgebungsvariable fest.  
  
-   Fügen Sie der VSPerfReport\-Befehlszeile die **\/SymbolPath**\-Option hinzu.  
  
 Sie können auch beide Methoden verwenden.  
  
> [!NOTE]
>  Wenn [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auf dem lokalen Computer installiert ist, wurde wahrscheinlich bereits ein Speicherort für die Windows\-Symboldateien angegeben.  Weitere Informationen finden Sie unter [Gewusst wie: Verweisen auf Windows\-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md).  Sie müssen dann noch VSPerfReport konfigurieren, um den Speicherort und den Server zu verwenden, wie weiter unten in diesem Thema beschrieben.  
  
## Angeben von Windows\-Symboldateien  
  
#### So konfigurieren Sie die Verwendung des Windows\-Symbolservers  
  
1.  Erstellen Sie ggf. ein Verzeichnis, um die Symboldateien lokal zu speichern.  
  
2.  Legen Sie die **\_NT\_SYMBOL\_PATH**\-Umgebungsvariable oder die VSPerfReport \/SymbolPath\-Option mithilfe der folgenden Syntax fest:  
  
     **srv\*** *LocalStore* **\*http:\/\/msdl.microsoft.com\/downloads\/symbols**  
  
     wobei *LocalStore* der Pfad des lokalen Verzeichnisses, das Sie erstellt haben.  
  
## Angeben von Komponentensymboldateien  
 Von den Profilerstellungstools wird nach den PDB\-Dateien der Komponenten, für die Sie ein Profil erstellen möchten, an den ursprünglichen Speicherorten gesucht, die in den Komponenten oder im Ordner mit der Profilerstellungs\-Datendatei gespeichert sind.  Sie können andere Speicherorte zum Durchsuchen angeben, indem Sie **\_NT\_SYMBOL\_PATH** oder der Option **\/SymbolPath** mindestens einen Pfad hinzufügen.  Separate Pfade mit Semikolons.  
  
## Beispiel  
 Die folgende Befehlszeile legt die **\_NT\_SYMBOL\_PATH**\-Umgebungsvariable auf den Windows\-Symbolserver und das lokale Verzeichnis auf **C:\\Symbols** fest.  
  
 **set  \_NT\_SYMBOL\_PATH\=srv\*C:\\symbols\*http:\/\/msdl.microsoft.com\/downloads\/symbols**  
  
 Die folgende VSPerfReport\-Befehlszeile fügt dem Suchpfad mit der **\/SymbolPath**\-Option das Verzeichnis "C:\\Projects\\Symbols" hinzu.  
  
 **VSPerfReport**  *MyApp* **.exe \/SymbolPath:C:\\Projects\\Symbols \/summary:all**