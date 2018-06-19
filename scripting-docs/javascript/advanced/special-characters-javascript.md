---
title: Sonderzeichen (JavaScript) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- line terminator character
- white space character
- Unicode character
- escape sequence
- backslash (\)
ms.assetid: 3b38b1bd-1f0f-4748-b13e-55cab36fd126
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0eaae8dfc84d9a3be6db54c50558d4cf675a53a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569630"
---
# <a name="special-characters-javascript"></a>Sonderzeichen (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] stellt Escapesequenzen bereit, die Sie in Zeichenfolgen einfügen können, um Zeichen zu erstellen, die nicht direkt eingegeben werden können.  
  
## <a name="remarks"></a>Hinweise  
 Ein Zeichenfolgenwert besteht aus null oder mehr Unicode-Zeichen (Buchstaben, Ziffern und andere Zeichen). Zeichenfolgenliterale werden in entsprechenden Paaren einfacher oder doppelter Anführungszeichen eingeschlossen. Doppelte Anführungszeichen können in einer Zeichenfolge enthalten sein, die in einfache Anführungszeichen eingeschlossen ist. Einfache Anführungszeichen können in einer Zeichenfolge enthalten sein, die in doppelte Anführungszeichen eingeschlossen ist.  
  
 Jedes Zeichen in einem Zeichenfolgenliteral kann durch eine Escapesequenz dargestellt werden. Eine Escapesequenz beginnt mit einem umgekehrten Schrägstrich (\\), mit dem Sie den [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Interpreter darüber informieren, dass das nächste Zeichen ein Sonderzeichen ist.  
  
 Sie können mit der Escapesequenz \u*hhhh* ein Unicode-Zeichen angeben, wobei *hhhh* eine vierstellige Hexadezimalzahl ist. Mit einer Unicode-Escapesequenz können beliebige 16-Bit-Zeichen dargestellt werden. Weitere Informationen finden Sie unter [Unicode-Codepunkt-Escapesequenzen](#CodePoint).  
  
 Für einige Zeichen kann eine Escapesequenz mit einem Zeichen verwendet werden. So gibt beispielsweise \t ein Tabstoppzeichen an.  
  
## <a name="escape-sequences"></a>Escapesequenzen  
 In der folgende Tabelle sind einige Beispiele für Escapesequenzen für allgemeine Zeichen aufgeführt.  
  
|Unicode-Zeichenwert|Escapesequenz|Bedeutung|Kategorie|  
|-----------------------------|---------------------|-------------|--------------|  
|\u0008|\b|Rückschritt||  
|\u0009|\t|Registerkarte|Leerraum|  
|\u000A|\n|Zeilenvorschub (Zeilenumbruch)|Zeilenabschlusszeichen|  
|\u000B|\v<br /><br /> (Siehe Hinweis nach dieser Tabelle.)|Vertikaler Tabulator|Leerraum|  
|\u000C|\f|Seitenvorschub|Leerraum|  
|\u000D|\r|Wagenrücklauf|Zeilenabschlusszeichen|  
|\u0020||Leerzeichen|Leerraum|  
|\u0022|\\"|Doppeltes Anführungszeichen (")||  
|\u0027|\\'|Einfaches Anführungszeichen (')||  
|\u005C|\\\|Umgekehrter Schrägstrich (\\)||  
|\u00A0||Geschütztes Leerzeichen|Leerraum|  
|\u2028||Zeilenseparator|Zeilenabschlusszeichen|  
|\u2029||Absatzseparator|Zeilenabschlusszeichen|  
|\uFEFF||Bytereihenfolge-Marke|Leerraum|  
  
 In der Kategoriespalte wird angegeben, ob das Zeichen ein Leerzeichen oder ein Zeilenabschlusszeichen ist. Mit der [trim-Methode (Zeichenfolge)](../../javascript/reference/trim-method-string-javascript.md) werden führende und nachfolgende Leerstellen- und Zeilenabschlusszeichen aus einer Zeichenfolge entfernt.  
  
 Der umgekehrte Schrägstrich (\) wird als Escapezeichen verwendet. Daher können Sie diesen nicht direkt in ein Skript eingeben. Wenn Sie einen umgekehrten Schrägstrich schreiben möchten, müssen Sie zwei aufeinander folgende umgekehrte Schrägstriche eingeben (\\\\).  
  
> [!NOTE]
>  Ab [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] können Sie den Browser nicht als Internet Explorer identifizieren, indem Sie auf die Übereinstimmung des vertikalen Tabstopps (\v) und des „v“ testen. In früheren Versionen gab der Ausdruck `"\v" === "v"` `true` zurück. In [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] gibt der Ausdruck `false` zurück.  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung  
 Im folgenden Beispiel werden die Escapesequenzen \\\ und \\' veranschaulicht.  
  
### <a name="code"></a>Code  
  
```JavaScript  
document.write('The image path is C:\\webstuff\\mypage\\gifs\\garden.gif.');  
document.write ("<br />");  
document.write('The caption reads, "After the snow of \'97. Grandma\'s house is covered."');  
```  
  
<a name="CodePoint"></a>   
## <a name="unicode-code-point-escape-sequences"></a>Unicode-Codepunkt-Escapesequenzen  
 In [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] wird Unicode vollständig unterstützt. Die am häufigsten verwendeten Unicode-Codepunkte werden durch vier hexadezimale Ziffern dargestellt, z. B. /u0009 für ein Tabstoppzeichen. Astrale Codepunkte, die alle Symbole enthalten, die mehr als vier hexadezimale Ziffern erfordern, werden jetzt in einem vereinfachten Format unterstützt. Mit dem Format „\u{*codepoint*}“ kann der vollständige Unicode-Zeichensatz in einem Literalformat dargestellt werden. Verwenden Sie z.B. das Format „\u{20BB7}“, um das Symbol „𠮷“ darzustellen.  
  
 Im folgenden Codebeispiel sind alle Zeichenfolgen äquivalent. (\uD842\uDFB7 ist die Problemumgehungsmethode zum Angeben dieses Symbols in früheren Versionen.)  
  
```JavaScript  
"\u{20BB7}"=="𠮷"=="\uD842\uDFB7"  
```  
  
 RegExp enthält jetzt ein /u-Flag, um vollständige Unterstützung für astrale Codepunkte zu ermöglichen. Im folgenden Codebeispiel beispielsweise ermöglicht das /u-Flag im regulären Ausdruck den Abgleich von astralen Punkten (der Punkt entspricht einem beliebigen Zeichen aus der angegebenen Zeichenfolge).  
  
```JavaScript  
"𠮷".match(/./u)[0].length == 2  
```  
  
 Das /u-Flag ermöglicht das Parsen des neuen Formats, \u{codepoint}), als Unicode-Escapesequenz. Dies ist erforderlich, da \u{xxxxx} ohne das /u-Flag in einem regulären Ausdruck eine andere Bedeutung hat.  
  
> [!NOTE]
>  Für astrale Codepunkt entspricht die Länge immer 2. Das entspricht dem Verhalten in früheren Versionen.  
  
 Das String-Objekt enthält nun zwei neue Methoden, String.codePointAt und String.fromCodePoint, zur Unterstützung von astralen Codepunkten. Sie können z.B. „codePointAt“ verwenden, um die Codepunkt-Entsprechung für das Symbol „𠮷“ zurückzugeben.  
  
```JavaScript  
"𠮷".codePointAt(0) == 0x20BB7  
  
```  
  
 Sie können Codepunkte auch mit der `for...of`-Anweisung durchlaufen.  
  
```JavaScript  
for(var c of "𠮷") {  
    console.log(c);  
}  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [String.fromCharCode-Funktion](../../javascript/reference/string-fromcharcode-function-javascript.md)