---
title: "Gewusst wie: &#196;ndern des Buildausgabeverzeichnisses | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ausgabeverzeichnis, Ändern"
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: &#196;ndern des Buildausgabeverzeichnisses
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können den Speicherort der vom das Projekt generierten Ausgabe auf Basis der Konfiguration \(„Debug“, „Release“ oder beides\) angeben.  
  
> [!NOTE]
>  Wenn Sie über ein **Setup**\-Projekt verfügen, beachten Sie den Hinweis am Ende dieses Artikels.  
  
## Ändern des Buildausgabeverzeichnisses  
  
#### So ändern Sie das Buildausgabeverzeichnis  
  
1.  Wählen Sie in der Menüleiste **Projekt** und die Option *App\-Name***Eigenschaften** aus. Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus.  
  
2.  Wenn Sie ein Visual Basic\-Projekt haben, wählen Sie die Registerkarte **Kompilieren**. Wenn Sie ein Visual C\#\-Projekt haben, wählen Sie die Registerkarte **Build**. Wenn Sie ein C\+\+\-Projekt oder ein JavaScript\-Projekt haben, wählen Sie die Registerkarte  **Allgemein**.  
  
3.  Wählen Sie in der Konfigurationen\-Dropdownliste am oberen Rand die Konfiguration aus, deren Speicherort der Ausgabedatei Sie ändern möchten \(„Debug“, „Release“ oder beides\).  
  
     Suchen Sie den Eintrag des Ausgabe\-Pfads \(**Buildausgabepfad** in Visual Basic **Ausgabeverzeichnis** in Visual C\+\+ **Ausgabepfad** in JavaScript und C\#\). Geben Sie ein neues Buildausgabeverzeichnis relativ zum Projektverzeichnis an.  
  
> [!NOTE]
>  In einem Setup\-Projekt wird durch das Feld **Ausgabedateiname** lediglich der Speicherort der Datei „Setup.exe“ und nicht der Speicherort der Projektdateien geändert. Weitere Informationen finden Sie unter **Erstellen, Konfigurationseigenschaften, Bereitstellungsprojekt\-Eigenschaften \(Dialogfeld\)**.  
  
## Siehe auch  
 [Seite "Erstellen", Projekt\-Designer \(C\#\)](../ide/reference/build-page-project-designer-csharp.md)   
 [Eigenschaftenseite "Allgemein" \(Projekt\)](/visual-cpp/ide/general-property-page-project)   
 [Anwendungen in Visual Studio erstellen](../ide/compiling-and-building-in-visual-studio.md)