---
title: "Vorgehensweise: Angeben von Symboldateispeicherorten über die Befehlszeile | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 63aad78bdc7df685ca3a73ec16a9cbc87b78151f
ms.openlocfilehash: 237acc5cc58646bc9f4e1ab6d2fbe976bb7ac124
ms.contentlocale: de-de
ms.lasthandoff: 07/14/2017

---
# Gewusst wie: Angeben von Symboldateispeicherorten über die Befehlszeile
<a id="how-to-specify-symbol-file-locations-from-the-command-line" class="xliff"></a>
Um Symbolinformationen, wie z.B. Funktionsnamen und Zeilennummern anzuzeigen, benötigt das VSPerfReport-Befehlszeilentool Zugriff auf die Symboldateien (.pdb) der profilierten Komponenten und die Windows-Systemdateien. Symboldateien werden erstellt, wenn eine Komponente kompiliert wird. Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport sucht automatisch in den folgenden Speicherorten nach Symboldateien:  
  
-   Angegeben Pfade in der **/SymbolPath**-Option oder in der **_NT_SYMBOL_PATH**-Umgebungsvariable.  
  
-   Der genaue lokale Pfad, in dem eine Komponente kompiliert wurde.  
  
-   Das Verzeichnis, das die Profilerstellungsdatendatei (.vsp oder .vsps) enthält.  
  
 Microsoft stellt die PDB-Dateien für viele seiner Produkte online auf einem Symbolserver bereit. Wenn der Computer, den Sie für die Berichterstattung verwenden, mit dem Internet verbunden ist, verbindet sich VSPerfReport mit dem Online-Symbolserver, um automatisch nach Symbolinformationen zu suchen und die Dateien in einem lokalen Speicher zu speichern.  
  
 Sie können den Speicherort der Symboldateien und den Microsoft-Symbolserver folgendermaßen angeben:  
  
-   Legen Sie die **_NT_SYMBOL_PATH**-Umgebungsvariable fest.  
  
-   Fügen Sie die **/SymbolPath**-Option zur VSPerfReport-Befehlszeile hinzu.  
  
 Sie können auch beide Methoden verwenden.  
  
> [!NOTE]
>  Wenn [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auf dem lokalen Computer installiert ist, wurde wahrscheinlich bereits ein Speicherort für die Windows-Symboldateien angegeben. Weitere Informationen finden Sie unter [Vorgehensweise: Verweisen auf Windows-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md). Sie müssen VSPerfReport dennoch konfigurieren, um den Speicherort und den Server, wie weiter unten in diesem Thema beschrieben, zu verwenden.  
  
## Angeben von Windows-Symboldateien
<a id="specifying-windows-symbol-files" class="xliff"></a>  
  
#### So konfigurieren Sie die Verwendung des Windows-Symbolservers
<a id="to-configure-the-use-of-the-windows-symbol-server" class="xliff"></a>  
  
1.  Falls erforderlich, erstellen Sie ein Verzeichnis, um die Symboldateien lokal zu speichern.  
  
2.  Verwenden Sie die folgende Syntax zum Festlegen der **_NT_SYMBOL_PATH**-Umgebungsvariable oder die VSPerfReport /SymbolPath-Option:  
  
     **srv\*** *LocalStore* **\*http://msdl.microsoft.com/downloads/symbols**  
  
     wobei *LocalStore* der Pfad des lokalen Verzeichnisses ist, das Sie erstellt haben.  
  
## Angeben von Komponentensymboldateien
<a id="specifying-component-symbol-files" class="xliff"></a>  
 Profilerstellungstools suchen nach den PDB-Dateien der Komponenten, die Sie in ihren ursprünglichen Speicherorten erstellen möchten, die in den Komponenten oder in den Ordnern mit der Profilerstellungsdatendatei gespeichert werden. Sie können andere Speicherorte zum Suchen angeben, indem Sie eine oder mehrere Pfade zu **_NT_SYMBOL_PATH** oder der **/SymbolPath**-Option hinzufügen. Separate Pfade mit Semikolons.  
  
## Beispiel
<a id="example" class="xliff"></a>  
 Die folgende Befehlszeile legt die **_NT_SYMBOL_PATH**-Umgebungsvariable auf den Windows-Symbolserver und das lokale Verzeichnis auf **C:\Symbols**.  
  
 **set  _NT_SYMBOL_PATH=srv\*C:\symbols\*http://msdl.microsoft.com/downloads/symbols**  
  
 Die folgende VSPerfReport-Befehlszeile fügt mithilfe der **/SymbolPath**-Option das Verzeichnis C:\Projects\Symbols zum Suchpfad hinzu.  
  
 **VSPerfReport**  *MyApp* **.exe /SymbolPath:C:\Projects\Symbols /summary:all**
