---
title: "Beseitigung von ~ SAK-Dateien | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Temporäre Dateien"
  - "~ Sak-Dateien"
  - "Source Control-Plug-ins ~ SAK-Dateien"
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Beseitigung von ~ SAK-Dateien
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Quellcodeverwaltungs\-Plug\-In API 1.2, ist die Anzahl von Dateien ~SAK Flags für Funktionen und neuen Funktionen ersetzt, die ermitteln, ob ein Quellcodeverwaltungs\-Plug\-In die MSSCCPRJ\-Datei und freigegebenen Auschecken unterstützt.  
  
## ~SAK Dateien  
 Visual Studio .NET 2003 erstellte temporäre Dateien, die mit ~SAK vorangestellt wurde.  Diese Dateien werden verwendet, um zu bestimmen, ob ein Quellcodeverwaltungs\-Plug\-In unterstützt:  
  
-   Die MSSCCPRJ.SCC\-Datei.  
  
-   Mehrere \(Shared\) Auschecken.  
  
 Für Plug\-Ins, die unterstützen, die erweiterte Features im Quellcodeverwaltungs\-Plug\-In API 1.2, der IDE können diese Funktionen zur Verfügung zu erkennen, ohne die temporären Dateien zu erstellen, durch die Verwendung von Flags, neuen Features und Funktionen einzeln in den folgenden Abschnitten beschrieben.  
  
## Neue Funktions\-Flags  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## Neue Funktionen  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Wenn ein Quellcodeverwaltungs\-Plug\-In mehrere \(freigegebenes\) Auschecken unterstützt, die `SCC_CAP_MULTICHECKOUT`\-Funktion deklariert und implementiert die `SccIsMultiCheckOutEnabled`\-Funktion.  Diese Funktion wird aufgerufen, wenn ein Auscheckvorgang auf einem der der Quellcodeverwaltung unterliegen Projekten auftritt.  
  
 Wenn ein Quellcodeverwaltungs\-Plug\-In die Erstellung und Verwendung einer MSSCCPRJ.SCC\-Datei unterstützt, die `SCC_CAP_SCCFILE`\-Funktion deklariert und implementiert [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md).  Diese Funktion wurde mit einer Liste von Dateien bezeichnet.  Die Funktion gibt `TRUE/FALSE` zurück, sodass jede Datei angibt, ob Visual Studio eine MSSCCPRJ.SCC\-Datei für das Steuerelement verwenden soll.  Wenn das Quellcodeverwaltungs\-Plug\-In beschließt, um diese neuen Features und Funktionen zu unterstützen, kann es nicht den folgenden Registrierungsschlüssel verwenden, um die Erstellung dieser Dateien zu deaktivieren:  
  
 \[HKEY\_CURRENT\_USER \\ Software \\ Microsoft \\ VisualStudio \\ 8.0 \\ SourceControl\] " DoNotCreateTemporaryFilesInSourceControl „\=dword: 00000001  
  
> [!NOTE]
>  Wenn dieser Registrierungsschlüssel zum steht " dword festgelegt ist: 00000000, wird er nach dem Schlüssel nicht vorhanden ist, und Visual Studio weiterhin versucht, die temporären Dateien zu erstellen.  Wenn jedoch der in einem DWORD auf den Registrierungsschlüssel festgelegt wird: 00000001, Visual Studio versucht nicht, die temporären Dateien zu erstellen.  Stattdessen verwendet er an, dass das Quellcodeverwaltungs\-Plug\-In nicht die MSSCCPRJ.SCC\-Datei unterstützt und nicht freigegebenen Auschecken unterstützt.  
  
## Siehe auch  
 [Was ist neu in Source Control\-Plug\-in API\-Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)