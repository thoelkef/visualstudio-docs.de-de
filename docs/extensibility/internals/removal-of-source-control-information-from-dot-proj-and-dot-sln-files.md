---
title: Entfernen von Informationen der Quellcodeverwaltung aus. Proj und. Sln-Dateien | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4caa3d9edd7cba768f6338ad7aecf168041a1130
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602922"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Entfernen von Informationen der Quellcodeverwaltung aus PROJ- und SLN-Dateien
In Version 1.2 von die Source-Plug-in-API SCC werden die Informationen in einem MSSCCPRJ gespeichert. SCC-Datei. Der Vorteil der MSSCCPRJ. SCC-Datei ist, dass die SCC-Informationen ist nicht im Quellmodell - gesteuert, wie in proj- und sln-Dateien.

## <a name="version-12-changes"></a>Versionsänderungen 1.2
 Im Quellcodeverwaltungs-Plug-ins, die auf die Datenquellen-Steuerelement-Plug-in API-Version 1.1 basieren, werden die Informationen zur Versionskontrolle in den Projektdateien (proj) und Projektmappendateien (.sln) gespeichert. Speicherort der Datenbank, der die Informationen der quellcodeverwaltung wird durch die AuxPath angegeben, und bestimmte Position innerhalb der Datenbank durch Projektname angegeben ist. Dieses Verhalten kann nach dem Branch, Verzweigung oder Kopiervorgänge Probleme verursachen, da der Projektname in der Regel ungültige nach jedem dieser Vorgänge wären.

 In der Quelle-Plug-in-API Version 1.1 der IDE verwendet ~ SAK-Dateien zu erkennen, ob ein plug-in die MSSCCPRJ unterstützt. SCC-Methode zum Speichern von Informationen der quellcodeverwaltung. Die Source-Plug-in-API Version 1.2 stellt eine neue Funktion zum Erkennen der Unterstützung für MSSCCPRJ bereit. SCC-Datei ohne Verwendung einer ~ SAK-Datei. Weitere Informationen finden Sie unter [Beseitigung von ~ SAK-Dateien](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Siehe auch
- [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)