---
title: Wann werden Projekttypen erstellt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 861250dac25288f353cbd5c57f510bf67dadce70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703431"
---
# <a name="when-to-create-project-types"></a>Gründe für das Erstellen von Projekttypen
Das Erstellen eines neuen Projekttyps [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bietet eine Grundlage für das Anpassen für Ihre Benutzer. Das Erstellen eines neuen Projekttyps [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist jedoch nicht für alle Anpassungen erforderlich. Anhand der folgenden Richtlinien können Sie ermitteln, ob ein neuer Projekttyp für Ihr Szenario erforderlich ist.

## <a name="create-a-new-project-type"></a>Erstellen eines neuen Projekttyps
 Sie müssen einen Projekttyp erstellen, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wenn Sie anpassen möchten, um auf eine oder mehrere der folgenden Arten zu handeln:

- Nehmen Sie an Build, Bereitstellung, Konfigurationen und Quellcodeverwaltung teil.

- Bieten Sie Debugging-Unterstützung an.

- Projektelemente im **Projektmappen-Explorer**anzeigen .

- Verwenden Sie das Dialogfeld **Projekt** öffnen oder **neues Projekt.**

- Unterstützen Sie die Verschachtelung von Projekten.

## <a name="extend-an-existing-project-type"></a>Erweitern eines vorhandenen Projekttyps
 Sie können einen neuen Projekttyp erstellen, der auf folgende Weise verwendet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] werden kann, um das Verhalten eines [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vorhandenen Projekttyps zu ändern oder zu erweitern, z. B. den Buildprozess für Projekte zu ändern:

- Arbeiten Sie mit mehreren Dateien als eine Einheit.

- Zeigen Sie eine einzelne Datei als Hierarchie von Unterelementen an.

- Zeigen Sie einen Befehlskontext um Editoren an.

- Zeigen Sie einen Dienstkontext für Editoren an.

## <a name="use-an-existing-project-type"></a>Verwenden eines vorhandenen Projekttyps
 Das Erstellen eines neuen Projekts ist manchmal nicht erforderlich. Die folgende Tabelle zeigt die Vorgänge, für die Sie keinen Projekttyp erstellen müssen.

|Aufgabe|BESCHREIBUNG|
|----------|-----------------|
|Umgang mit Befehlen|Jedes VSPackage kann Befehle verarbeiten.|
|Erstellen eines Editors|Benutzerdefinierte Editoren können registriert werden. Weitere Informationen finden Sie unter [Dokument Windows und Editoren](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc).|
|Besitzen von Fenstern|Sie können sowohl Werkzeug- als auch Dokumentfenster erstellen, ohne einen neuen Projekttyp hinzuzufügen.|
|Offenlegen von Eigenschaften im Fenster Eigenschaften|Alle Objekte können Eigenschaften verfügbar machen.|

## <a name="create-a-project-subtype"></a>Erstellen eines Projektuntertyps
 Sie können Projektuntertypen verwenden, um einen verwalteten Projekttyp zu erweitern, ohne einen neuen Projekttyp erstellen zu müssen. Projektuntertypen verwenden COM-Aggregation, um [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] verwaltete Projekte zu erweitern, die in Microsoft oder [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]geschrieben wurden. Mit der COM-Aggregation können Sie einen Großteil der verwalteten Projektsystemimplementierung wiederverwenden und dennoch für ein bestimmtes Szenario durch Aggregation und die Verwendung unterstützender Schnittstellen anpassen. Weitere Informationen zu Projektuntertypen finden Sie unter [Projektuntertypen](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Weitere Informationen
- [Dokumentieren von Windows und Editoren](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
