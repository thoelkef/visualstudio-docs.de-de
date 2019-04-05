---
title: Formatbezeichner in C++ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- QuickWatch dialog box, format specifiers in C++
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- expressions [C++], format specifiers
- specifiers, watch variable format
- specifiers
- Watch window, format specifiers in C++
- watch variable symbols
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e7547f4c675bc7c68c61e86ef61a6285bfb65fb2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957204"
---
# <a name="format-specifiers-in-c"></a>Formatbezeichner in C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können das Format ändern, in dem ein Wert im Fenster **Überwachen** mithilfe von Formatbezeichnern angezeigt wird.  
  
 Formatbezeichner können im Fenster **Direkt** , im Fenster **Befehl** und sogar in den Quellcodefenstern verwendet werden. Wenn Sie in einen Ausdruck in diesen Fenstern anhalten, wird das Ergebnis in einem DataTip angezeigt. Die DataTip-Anzeige entspricht dem Formatbezeichner.  
  
> [!NOTE]
>  Der systemeigene Debugger in Visual Studio wurde als neue Debug-Engine konstruiert. Im Rahmen dieser Änderung wurden mehrere neue Formatbezeichner hinzugefügt und einige alte Formatbezeichner entfernt. Der ältere Debugger wird weiterhin verwendet, wenn Sie das Interop-Debuggen (systemeigen und verwaltet) mit C++/CLI durchführen. Folgende Abschnitte in diesem Thema erläutern die Formatbezeichner für jede Debug-Engine.  
> 
> - [Formatbezeichner](#BKMK_Visual_Studio_2012_format_specifiers) werden die Formatbezeichner in der neuen Debug-Engine beschrieben.  
>   -   [Formatbezeichner für das Interop-Debuggen mit C++/CLI](#BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue) werden die Formatbezeichner in der älteren Debug-Engine beschrieben.  
  
## <a name="using-format-specifiers"></a>Verwenden von Formatbezeichnern  
 Wenn Ihr Code folgendermaßen lautet:  
  
```cpp  
int main() {  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Fügen Sie die Variable `my_var1` dem Fenster **Überwachen** hinzu (beim Debugging, **Debuggen / Windows / Überwachen / Überwachen 1**), und legen Sie die Anzeige auf hexadezimal fest (klicken Sie im Fenster **Überwachen** mit der rechten Maustaste auf die Variable, und wählen Sie **Hexadezimale Anzeige**aus). Im Fenster "Überwachen" wird nun angezeigt, dass der Wert 0x0065 enthalten ist. Um diesen Wert als Zeichen und nicht als ganze Zahl anzuzeigen, geben Sie in der Spalte "Name" hinter dem Variablennamen den Zeichenformatbezeichner **, c**ein. In der Spalte **Wert** wird nun **101 'e'** angezeigt.  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
##  <a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Formatbezeichner  
 Die folgenden Tabellen zeigen die Formatbezeichner, dass Sie in Visual Studio verwenden können. Fett formatierte Bezeichner werden nicht für das Interop-Debuggen mit C++/CLI unterstützt.  
  
|Bezeichner|Format|Ursprünglicher Wert in "Überwachen"|Angezeigter Wert|  
|---------------|------------|--------------------------|---------------------|  
|T|Ganze Dezimalzahl|0x00000066|102|  
|o|Oktale ganze Zahl ohne Vorzeichen|0x00000066|000000000146|  
|w<br /><br /> **h**|Ganze Hexadezimalzahl|102|0xcccccccc|  
|X<br /><br /> **H**|Ganze Hexadezimalzahl|102|0xcccccccc|  
|c|Einzelnes Zeichen|0x0065, c|101 'e'|  
|s|const char*-Zeichenfolge|\<Speicherort > "Hello World"|"hello world"|  
|**sb**|const char*-Zeichenfolge|\<Speicherort > "Hello World"|hello world|  
|s8|const char*-Zeichenfolge|\<Speicherort > "Hello World"|"hello world"|  
|**s8b**|const char*-Zeichenfolge|\<Speicherort > "Hello World"|"hello world"|  
|su|const Wchar_t * const<br /><br /> char16_t\* Zeichenfolge|\<Speicherort > L "Hello World"|L"hello world"<br /><br /> u"hello world"|  
|sub|const Wchar_t * const<br /><br /> char16_t\* Zeichenfolge|\<Speicherort > L "Hello World"|hello world|  
|bstr|BSTR-Zeichenfolge|\<Speicherort > L "Hello World"|L”hello world”|  
|**s32**|UTF-32-Zeichenfolge|\<Speicherort > U "Hello World"|U”hello world”|  
|**s32b**|UTF-32-Zeichenfolge (ohne Anführungszeichen)|\<Speicherort > U "Hello World"|hello world|  
|**en**|enum|Samstag(6)|Samstag|  
|**hv**|Zeigertyp - gibt an, dass der überprüfte Zeigerwert das Ergebnis der Heapzuweisung eines Arrays ist, z. B. `new int[3]`.|\<Speicherort>{\<Erster Member>}|\<Speicherort > {\<erste Member >, \<zweite Member >,...}|  
|**na**|Unterdrückt die Speicheradresse eines Zeigers auf ein Objekt.|\<location>, {member=value…}|{member=value…}|  
|**nd**|Es werden nur die Basisklasseninformationen angezeigt, die abgeleiteten Klassen werden ignoriert.|`(Shape*) square` enthält die Basisklassen- und abgeleitete Klasseninformationen|Zeigt nur Basisklasseninformationen an|  
|hr|HRESULT oder Win32-Fehlercode. (Der Debugger decodiert HRESULT-Werte nun automatisch, sodass der Bezeichner in diesem Fall nicht erforderlich ist.)|S_OK|S_OK|  
|wc|Fensterklassenflag|0x0010|WC_DEFAULTCHAR|  
|wm|Windows-Meldungsnummern|16|WM_CLOSE|  
|!|Rohdatenformat, jegliche Ansichtsanpassungen für den Datentyp werden ignoriert.|\<Benutzerdefinierte Darstellung>|4|  
  
> [!NOTE]
>  Wenn der Formatbezeichner **hv** vorhanden ist, versucht der Debugger, die Länge des Puffers zu bestimmen, und zeigt die entsprechende Anzahl von Elementen an. Da der Debugger nicht immer die exakte Puffergröße eines Arrays finden kann, sollten Sie möglichst immer einen Größenbezeichner `(pBuffer,[bufferSize])` verwenden. Der Formatbezeichner **hv** ist für Szenarien vorgesehen, in denen die Puffergröße nicht einfach verfügbar ist.  
  
###  <a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Größenbezeichner für Zeiger als Arrays  
 Wenn Sie einen Zeiger für ein Objekt haben, das Sie als Array anzeigen möchten, können Sie eine ganze Zahl oder einen Ausdruck verwenden, um die Anzahl von Arrayelementen zu bestimmen:  
  
|Bezeichner|Format|Ursprünglicher Wert in "Überwachen"|Angezeigter Wert|  
|---------------|------------|---------------------------|---------------------|  
|n|Dezimalzahl oder ganze **Hexadezimalzahl**|pBuffer,[32]<br /><br /> pBuffer,**[0x20]**|Zeigt `pBuffer` als Array mit 32 Elementen an.|  
|**[exp]**|Ein gültiger C++-Ausdruck, der für eine ganze Zahl ausgewertet wird.|pBuffer,[bufferSize]|Zeigt pBuffer als Array von `bufferSize` Elementen an.|  
|**expand(n)**|Ein gültiger C++-Ausdruck, der für eine ganze Zahl ausgewertet wird|pBuffer, expand(2)|Zeigt das dritte Element von  `pBuffer`an|  
  
##  <a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Formatbezeichner für das Interop-Debuggen mit C++/CLI  
 **Fett formatierte** Bezeichner werden nur zum Debuggen von systemeigenem und C++/CLI-Code unterstützt.  
  
|Bezeichner|Format|Ursprünglicher Wert in "Überwachen"|Angezeigter Wert|  
|---------------|------------|--------------------------|---------------------|  
|**d,i**|Ganze Dezimalzahl mit Vorzeichen|0xF000F065|-268373915|  
|**n**|Ganze Dezimalzahl ohne Vorzeichen|0x0065|101|  
|o|Oktale ganze Zahl ohne Vorzeichen|0xF065|0170145|  
|x,X|Ganze Hexadezimalzahl|61541|0x0000f065|  
|**l,h**|Langes oder kurzes Präfix für: d, i, u, o, x, X|00406042|0x0c22|  
|**f**|Gleitkommazahl mit Vorzeichen|(3./2.), f|1.500000|  
|**e**|Wissenschaftliche Notation mit Vorzeichen|(3.0/2.0)|1.500000e+000|  
|**g**|Gleitkommazahl oder wissenschaftliche Notation mit Vorzeichen, je nachdem, welche kürzer ist|(3.0/2.0)|1.5|  
|c|Einzelnes Zeichen|\<Speicherort>|101 'e'|  
|s|const char*|\<Speicherort>|"hello world"|  
|su|const wchar_t*<br /><br /> const char16_t\*|\<Speicherort>|L"hello world"|  
|sub|const wchar_t*<br /><br /> const char16_t\*|\<Speicherort>|hello world|  
|s8|const char*|\<Speicherort>|"hello world"|  
|hr|HRESULT oder Win32-Fehlercode. (Der Debugger decodiert HRESULT-Werte nun automatisch, sodass der Bezeichner in diesem Fall nicht erforderlich ist.)|S_OK|S_OK|  
|wc|Fensterklassenflag|0x00000040,|WC_DEFAULTCHAR|  
|wm|Windows-Meldungsnummern|0x0010|WM_CLOSE|  
|!|Rohdatenformat, jegliche Ansichtsanpassungen für den Datentyp werden ignoriert.|\<Benutzerdefinierte Darstellung>|4|  
  
###  <a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Formatbezeichner für Speicherbereiche beim Interop-Debuggen mit C++/CLI  
 Die folgende Tabelle enthält Formatierungssymbole, die für Speicherbereiche verwendet werden. Bezeichner für Speicherbereiche können mit beliebigen Werten oder Ausdrücken verwendet werden, die als Speicherbereiche ausgewertet werden.  
  
|Symbol|Format|Ursprünglicher Wert in "Überwachen"|Angezeigter Wert|  
|------------|------------|--------------------------|---------------------|  
|**ma**|64 ASCII-Zeichen|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|  
|**m**|16 Bytes im Hexadezimalformat, gefolgt von 16 ASCII-Zeichen|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|  
|**mb**|16 Bytes im Hexadezimalformat, gefolgt von 16 ASCII-Zeichen|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|  
|**mw**|8 Wörter|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**md**|4 Doppelwörter|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|  
|**mq**|2 Vierfachwörter|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**mu**|2-Byte-Zeichen (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|  
  
###  <a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Größenbezeichner für Zeiger als Arrays beim Interop-Debuggen mit C++/CLIt  
 Wenn Sie einen Zeiger für ein Objekt haben, das Sie als Array anzeigen möchten, können Sie eine ganze Zahl verwenden, um die Anzahl von Arrayelementen zu bestimmen:  
  
|Bezeichner|Format|Ausdruck|Angezeigter Wert|  
|---------------|------------|----------------|---------------------|  
|n|Ganze Dezimalzahl|pBuffer[32]|Zeigt `pBuffer` als Array mit 32 Elementen an.|
