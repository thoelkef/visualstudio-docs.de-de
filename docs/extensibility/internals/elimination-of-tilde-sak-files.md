---
title: "Dadurch entfällt ~ SAK-Dateien | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e487acefcb06c4fa0cd2070bfcf20bd065d500ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="elimination-of-sak-files"></a>Dadurch entfällt ~ SAK-Dateien
Datenquellen-Steuerelement-Plug-in-API 1.2 die ~ SAK Dateien wurden durch die Funktion Flags und neue Funktionen, die erkennen, ob ein Quellcodeverwaltungs-Plug-in die MSSCCPRJ-Datei und die freigegebenen Auschecken unterstützt ersetzt.  
  
## <a name="sak-files"></a>~ SAK-Dateien  
 Visual Studio .NET 2003 erstellte temporäre Dateien, die mit dem Präfix ~ SAK. Diese Dateien werden verwendet, um festzustellen, ob ein Quellcodeverwaltungs-Plug-in unterstützt:  
  
-   Die MSSCCPRJ. SCC-Datei.  
  
-   Mehrfaches Auschecken (freigegeben).  
  
 Für Plug-ins, die erweiterte Funktionen in der Quelle Steuerelement-Plug-in-API 1.2 unterstützen, kann die IDE Funktionen erkennen, ohne Erstellen der temporären Dateien durch die Verwendung von neuen Funktionen, Flags und Funktionen, die in den folgenden Abschnitten beschrieben.  
  
## <a name="new-capability-flags"></a>Neue Funktion Flags  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Neue Funktionen  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Wenn ein Quellcodeverwaltungs-Plug-in unterstützt (freigegebene) Mehrfaches, deklariert den `SCC_CAP_MULTICHECKOUT` Funktion und implementiert die `SccIsMultiCheckOutEnabled` Funktion. Diese Funktion wird aufgerufen, einen Auscheckvorgang auf keinem der Projekte quellcodeverwaltete eintreten.  
  
 Wenn ein Quellcodeverwaltungs-Plug-in die Erstellung und Verwendung von einem MSSCCPRJ unterstützt. Deklariert SCC-Datei, dann werden die `SCC_CAP_SCCFILE` Funktion und implementiert die [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Diese Funktion wird mit einer Liste von Dateien. Die Funktion gibt `TRUE/FALSE` für jede Datei, um anzugeben, ob ein MSSCCPRJ von Visual Studio verwendet werden soll. SCC-Datei für sie. Entscheidet das Quellsteuerelement-Plug-in nicht, um diese neuen Funktionen und Funktionen zu unterstützen, können sie den folgenden Registrierungsschlüssel verwenden, um die Erstellung dieser Dateien zu deaktivieren:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateTemporaryFilesInSourceControl" = DWORD: 00000001  
  
> [!NOTE]
>  Wenn dieser Registrierungsschlüssel auf DWORD: 00000000 festgelegt ist, entspricht dem wird nicht vorhandenen Schlüssel und Visual Studio weiterhin versucht wird, um die temporären Dateien zu erstellen. Jedoch, wenn der Registrierungsschlüssel auf DWORD: 00000001 festgelegt ist, Visual Studio versucht nicht, temporäre Dateien erstellt. Stattdessen wird angenommen, dass die Datenquellen-Steuerelements, das plug-in die MSSCCPRJ nicht unterstützt wird. SCC-Datei und unterstützt keine freigegebene Auschecken.  
  
## <a name="see-also"></a>Siehe auch  
 [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)