---
title: Beseitigung von ~ SAK-Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 930ee0690e14431298461f50387a94dd4bb0ce7d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780463"
---
# <a name="elimination-of-sak-files"></a>Beseitigung von ~SAK-Dateien
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Datenquellen-Steuerelement-Plug-in-API 1.2 die ~ SAK-Dateien wurden durch funktionsflags und neue Funktionen, die erkennen, ob ein Quellcodeverwaltungs-Plug-Ins, die MSSCCPRJ-Datei, und freigegebene ausgecheckte Elemente nicht unterstützt ersetzt.  
  
## <a name="sak-files"></a>~ SAK-Dateien  
 Visual Studio .NET 2003 erstellte temporäre Dateien, die mit dem Präfix ~ SAK. Diese Dateien werden verwendet, um festzustellen, ob ein Quellcodeverwaltungs-Plug-in unterstützt:  
  
- Die MSSCCPRJ. SCC-Datei.  
  
- Mehrfaches Auschecken (freigegeben).  
  
  Die IDE kann für Plug-ins, die erweiterten Funktionen in die Datenquellen-Steuerelement-Plug-in-API 1.2 zu unterstützen, diese Funktionen erkennen, ohne Erstellen der temporären Dateien durch die Verwendung von neuen Funktionen, Flags und Funktionen, die in den folgenden Abschnitten beschrieben.  
  
## <a name="new-capability-flags"></a>Neue Funktionsflags  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Neue Funktionen  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Wenn ein Quellcodeverwaltungs-Plug-in unterstützt Mehrfaches Auschecken (freigegebene), deklariert die `SCC_CAP_MULTICHECKOUT` Funktion und implementiert die `SccIsMultiCheckOutEnabled` Funktion. Diese Funktion wird aufgerufen, wenn ein Auschecken in keinem der Projekte quellcodeverwaltung ausgeführt wird.  
  
 Wenn ein Quellcodeverwaltungs-Plug-in die Erstellung und Verwendung einer MSSCCPRJ unterstützt. SCC-Datei, und klicken Sie dann diese deklariert die `SCC_CAP_SCCFILE` Funktion und implementiert die [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Diese Funktion wird eine Liste mit Dateien aufgerufen. Die Funktion gibt `TRUE/FALSE` für jede Datei, um anzugeben, ob Visual Studio ein MSSCCPRJ verwenden soll. SCC-Datei. Wenn das Quellcodeverwaltungs-Plug-in auswählt, nicht zu dieser neuen Funktionen und Funktionen zu unterstützen, können sie den folgenden Registrierungsschlüssel verwenden, um die Erstellung dieser Dateien zu deaktivieren:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateTemporaryFilesInSourceControl" = DWORD: 00000001  
  
> [!NOTE]
>  Wenn dieser Registrierungsschlüssel auf DWORD: 00000000 festgelegt ist, dies entspricht dem Schlüssel, die nicht vorhandene wird und Visual Studio weiterhin versucht wird, um die temporären Dateien zu erstellen. Jedoch, wenn der Registrierungsschlüssel auf DWORD: 00000001 festgelegt ist, Visual Studio versucht nicht, die temporären Dateien zu erstellen. Stattdessen wird angenommen, dass das Quellcodeverwaltungs-Plug-in die MSSCCPRJ nicht unterstützt wird. SCC-Datei und nicht freigegebene ausgecheckte Elemente nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

