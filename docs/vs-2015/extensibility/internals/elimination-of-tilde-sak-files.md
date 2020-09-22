---
title: Beseitigung von ~ Sak-Dateien | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 751acf4e5f56b7b477f05ab71571e0becd566649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840916"
---
# <a name="elimination-of-sak-files"></a>Beseitigung von ~SAK-Dateien
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In der Quellcodeverwaltungs-Plug-in-API 1,2 wurden die ~ Sak-Dateien durch funktionsflags und neue Funktionen ersetzt, die erkennen, ob ein Quellcodeverwaltungs-Plug-in die Mssccprj-Datei und freigegebene Auscheck Vorgänge unterstützt.  
  
## <a name="sak-files"></a>~ Sak-Dateien  
 Visual Studio .NET 2003 hat temporäre Dateien mit dem Präfix ~ Sak erstellt. Diese Dateien werden verwendet, um zu bestimmen, ob ein Quellcodeverwaltungs-Plug-in Folgendes unterstützt:  
  
- Mssccprj. SCC-Datei.  
  
- Mehrere (freigegebene) Checkouts.  
  
  Für Plug-ins, die erweiterte Funktionen unterstützen, die in der Quellcodeverwaltungs-Plug-in-API 1,2 bereitgestellt werden, kann die IDE diese Funktionen erkennen, ohne die temporären Dateien durch die Verwendung neuer Funktionen, Flags und Funktionen zu erstellen, die in den folgenden Abschnitten beschrieben werden.  
  
## <a name="new-capability-flags"></a>Neue funktionsflags  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Neue Funktionen  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Wenn ein Quellcodeverwaltungs-Plug-in mehrere (freigegebene) Checkouts unterstützt, deklariert es die `SCC_CAP_MULTICHECKOUT` Funktion und implementiert die- `SccIsMultiCheckOutEnabled` Funktion. Diese Funktion wird immer dann aufgerufen, wenn ein Auscheck Vorgang für eines der Projekte mit Quell Code Verwaltung ausgeführt wird.  
  
 Wenn ein Quellcodeverwaltungs-Plug-in die Erstellung und Verwendung von Mssccprj unterstützt. SCC-Datei, anschließend wird die `SCC_CAP_SCCFILE` Funktion deklariert und [sccwillkreatesccfile](../../extensibility/sccwillcreatesccfile-function.md)implementiert. Diese Funktion wird mit einer Liste von Dateien aufgerufen. Die Funktion gibt `TRUE/FALSE` für jede Datei zurück, um anzugeben, ob Visual Studio eine Mssccprj verwenden soll. SCC-Datei für die Datei. Wenn das Quellcodeverwaltungs-Plug-in diese neuen Funktionen und Funktionen nicht unterstützt, kann der folgende Registrierungsschlüssel verwendet werden, um die Erstellung dieser Dateien zu deaktivieren:  
  
 [HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0\sourcecontrol] "Donotkreatetemporaryfilesinsourcecontrol" = DWORD: 00000001  
  
> [!NOTE]
> Wenn dieser Registrierungsschlüssel auf DWORD: 00000000 festgelegt ist, entspricht er dem Schlüssel, der nicht vorhanden ist, und Visual Studio versucht weiterhin, die temporären Dateien zu erstellen. Wenn der Registrierungsschlüssel jedoch auf DWORD: 00000001 festgelegt ist, versucht Visual Studio nicht, die temporären Dateien zu erstellen. Stattdessen wird davon ausgegangen, dass das Quellcodeverwaltungs-Plug-in das Mssccprj nicht unterstützt. SCC-Datei und unterstützt keine freigegebenen Checkouts.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
