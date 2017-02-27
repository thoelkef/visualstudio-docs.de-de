---
title: "How to: Display an Item List Separated with Commas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, separating items with semicolons"
  - "MSBuild, formatting item collections"
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# How to: Display an Item List Separated with Commas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie mit Elementlisten in [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\) arbeiten, ist es zeitweise hilfreich, den Inhalt dieser Elementlisten in einer leicht lesbaren Form anzuzeigen.  Möglicherweise verfügen Sie aber auch über eine Aufgabe mit einer Liste von Elementen, die durch ein bestimmtes Trennzeichen getrennt sind.  In beiden Fällen können Sie ein Trennzeichen für eine Elementliste festlegen.  
  
## Trennen von Elementen in einer Liste mit Kommas  
 Standardmäßig verwendet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Semikolons, um Elemente in einer Liste zu trennen.  Angenommen, Sie verfügen über ein `Message`\-Element mit folgendem Wert:  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Wenn die `@(TXTFile)`\-Elementliste die Elemente App1.txt, App2.txt und App3.txt enthält, lautet die Meldung:  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Wenn Sie das Standardverhalten ändern möchten, können Sie ein eigenes Trennzeichen eingeben.  Die Syntax zum Festlegen eines Trennzeichens für Elementlisten lautet:  
  
 `@(ItemListName, '<separator>')`  
  
 Das Trennzeichen kann entweder ein einzelnes Zeichen oder eine Zeichenfolge sein und muss in einfache Anführungszeichen eingeschlossen werden.  
  
#### So fügen Sie ein Komma und ein Leerzeichen zwischen Elementen ein  
  
-   Verwenden Sie eine mit folgendem Beispiel vergleichbare Elementnotation:  
  
     `@(TXTFile, ', ')`  
  
## Beispiel  
 In diesem Beispiel wird das Tool findstr von der Aufgabe [Exec](../msbuild/exec-task.md) ausgeführt, um die angegebenen Textzeichenfolgen in der Datei Phrases.txt zu suchen.  Im findstr\-Befehl werden Zeichenfolgen für die wörtliche Suche durch den **\/c:**\-Schalter angegeben. Folglich wird das Elementtrennzeichen `/c:` zwischen Elementen in der `@(Phrase)`\-Elementliste eingefügt.  
  
 Der entsprechende Befehlszeilenbefehl für dieses Beispiel lautet:  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## Siehe auch  
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Items](../msbuild/msbuild-items.md)