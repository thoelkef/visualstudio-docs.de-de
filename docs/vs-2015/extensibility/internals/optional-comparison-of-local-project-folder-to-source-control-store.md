---
title: Optionaler Vergleich des lokalen Projekt Ordners mit dem Quellcodeverwaltungs-Speicher | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: be26b4195e0db7b3b78fcc2223ff2a6f8bde47d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841169"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Optionaler Vergleich des lokalen Projektordners mit dem Speicher der Quellcodeverwaltung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In der Quellcodeverwaltungs-Plug-in-API 1,2 wird der Vergleich zwischen dem lokalen Projektordner und der Quell Code Verwaltung mithilfe der Funktionen [sccdirqueryinfo](../../extensibility/sccdirqueryinfo-function.md) und [sccdirdiff](../../extensibility/sccdirdiff-function.md)durchgeführt.  
  
 Wenn Sie in **Projektmappen-Explorer**einen Ordner anstelle einer einzelnen Datei auswählen, ruft das Kontextmenü für die **Vergleichs Versionen** das neue [sccdirqueryinfo](../../extensibility/sccdirqueryinfo-function.md) -und [sccdirdiff](../../extensibility/sccdirdiff-function.md) -Element im Quellcodeverwaltungs-Plug-in auf.  
  
## <a name="new-capability-flags"></a>Neue funktionsflags  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Neue Funktionen  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 Die- `SccDirQueryInfo` Funktion wird vor aufgerufen `SccDirDiff` , um zu bestimmen, ob das Arbeitsverzeichnis Quell gesteuert ist. Die `SccDirDiff` -Funktion zeigt die Unterschiede zwischen dem aktuellen lokalen Verzeichnis und dem entsprechenden Ordner für die Quell Code Verwaltung an. Dieser Befehl fordert das Quellcodeverwaltungs-Plug-in auf, die Liste der Änderungen im Verzeichnis anzuzeigen. Ein Quellcodeverwaltungs-Plug-in stellt eine eigene Benutzeroberfläche zum Anzeigen der Unterschiede bereit.  
  
> [!NOTE]
> Diese Funktion verwendet die gleichen [Befehlsflags wie sccdiff](../../extensibility/sccdiff-function.md). Als Anbieter von Quellcodeverwaltungs-Plug-Ins können Sie den Vorgang für die schnelle diff-Ausführung für Verzeichnisse nicht unterstützen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
