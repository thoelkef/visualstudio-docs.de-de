---
title: Entfernen von Quell Code Verwaltungsinformationen aus proj-und SLN-Dateien
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a5f9b6ac83df104c381d7100a5e8fda5ac48a61
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90034675"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Entfernen von Quell Code Verwaltungsinformationen aus proj-und SLN-Dateien

In Version 1,2 der Quellcodeverwaltungs-Plug-in-API werden SCC-Informationen in einem Mssccprj gespeichert. SCC-Datei. Der Vorteil von Mssccprj. SCC File ist, dass die SCC-Informationen nicht Quell gesteuert werden, wie Sie sich in proj-und SLN-Dateien befinden.

## <a name="version-12-changes"></a>Änderungen der Version 1,2

 In Quellcodeverwaltungs-Plug-ins, die auf der API-Version 1,1 der Quellcodeverwaltungs-Plug-in basieren, werden Informationen zur Quell Code Verwaltung in den Projektdateien (. proj) und in Projektmappendateien (. sln) gespeichert. Der Speicherort der Quell Code Verwaltung wird durch den Pfad für die Quell Code Verwaltung festgelegt, und der angegebene Speicherort in der Datenbank wird von ProjName angegeben. Dieses Verhalten kann Probleme nach Verzweigungen, Verzweigungen oder Kopier Vorgängen verursachen, da der Proxy Name in der Regel nach einer dieser Vorgänge ungültig wäre.

 In der Quellcodeverwaltungs-Plug-in-API-Version 1,1 hat die IDE ~ Sak-Dateien verwendet, um zu erkennen, ob ein Plug-in Mssccprj unterstützt. SCC-Methode zum Speichern von Informationen zur Quell Code Verwaltung. Die API-Version 1,2 der Quellcodeverwaltungs-Plug-in bietet eine neue Funktion zum Erkennen der Unterstützung für Mssccprj. SCC-Datei ohne Verwendung einer ~ Sak-Datei. Weitere Informationen finden Sie unter [eliminieren von ~ Sak-Dateien](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Weitere Informationen

- [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
