---
title: Beseitigung von ~ SAK-Dateien | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 37d2d8fbbd98e75b398caec9e4c2f36a5853ba4a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53862813"
---
# <a name="elimination-of-sak-files"></a>Beseitigung von ~ SAK-Dateien
Im Datenquellen-Steuerelement-Plug-in-API 1.2 die *~ SAK* Dateien wurden durch funktionsflags ersetzt, und neue Funktionen, die erkennen, ob eine Quelle steuern-Plug-in unterstützt die *MSSCCPRJ* Datei- und freigegebene ausgecheckte Elemente nicht.  
  
## <a name="sak-files"></a>~ SAK-Dateien  
Visual Studio .NET 2003 erstellte temporäre Dateien, die mit dem Präfix *~ SAK*. Diese Dateien werden verwendet, um festzustellen, ob ein Quellcodeverwaltungs-Plug-in unterstützt:  
  
- Die *MSSCCPRJ.SCC* Datei.  
  
- Mehrfaches Auschecken (freigegeben).  
    
Die IDE kann für Plug-ins, die erweiterten Funktionen in die Datenquellen-Steuerelement-Plug-in-API 1.2 zu unterstützen, diese Funktionen erkennen, ohne Erstellen der temporären Dateien durch die Verwendung von neuen Funktionen, Flags und Funktionen, die in den folgenden Abschnitten beschrieben.  
  
## <a name="new-capability-flags"></a>Neue funktionsflags  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Neue Funktionen  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Wenn ein Quellcodeverwaltungs-Plug-in unterstützt Mehrfaches Auschecken (freigegebene), deklariert die `SCC_CAP_MULTICHECKOUT` Funktion und implementiert die `SccIsMultiCheckOutEnabled` Funktion. Diese Funktion wird aufgerufen, wenn ein Auschecken in keinem der Projekte quellcodeverwaltung ausgeführt wird.  
  
 Wenn ein Quellcodeverwaltungs-Plug-in unterstützt die Erstellung und Verwendung von ein *MSSCCPRJ.SCC* -Datei, und klicken Sie dann die es deklariert die `SCC_CAP_SCCFILE` Funktion und implementiert die [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Diese Funktion wird eine Liste mit Dateien aufgerufen. Die Funktion gibt `TRUE' or 'FALSE` für jede Datei, um anzugeben, ob Visual Studio verwenden, sollte ein *MSSCCPRJ.SCC* -Datei. Wenn das Quellcodeverwaltungs-Plug-in auswählt, nicht zu dieser neuen Funktionen und Funktionen zu unterstützen, können sie den folgenden Registrierungsschlüssel verwenden, um die Erstellung dieser Dateien zu deaktivieren:  
  
 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateTemporaryFilesInSourceControl** = *DWORD: 00000001*  
  
> [!NOTE]
>  Wenn dieser Registrierungsschlüssel, um festgelegt ist *DWORD: 00000000*, dies entspricht dem Schlüssel, die nicht vorhandene wird und Visual Studio weiterhin versucht wird, um die temporären Dateien zu erstellen. Jedoch, wenn der Registrierungsschlüssel, um festgelegt ist *DWORD: 00000001*, versucht Visual Studio nicht zur Erstellung der temporären Dateien. Stattdessen es wird davon ausgegangen, dass das Quellcodeverwaltungs-Plug-in nicht unterstützt. die *MSSCCPRJ.SCC* Datei und nicht freigegebene ausgecheckte Elemente nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Neuerungen in der Quelle Steuerelement-Plug-in-API-Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)