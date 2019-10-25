---
title: Zeitpunkt der Erstellung von Projekttypen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff29843965c220c505266a9cd973e5695c0b9dab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721553"
---
# <a name="when-to-create-project-types"></a>Gründe für das Erstellen von Projekttypen
Das Erstellen eines neuen Projekt Typs bietet eine Grundlage für die Anpassung [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] für Ihre Benutzer. Es ist jedoch nicht erforderlich, einen neuen Projekttyp für alle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Anpassungen zu erstellen. Die folgenden Richtlinien sollen Ihnen dabei helfen zu bestimmen, ob ein neuer Projekttyp für Ihr Szenario erforderlich ist.

## <a name="create-a-new-project-type"></a>Neuen Projekttyp erstellen
 Sie müssen einen Projekttyp erstellen, wenn Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] so anpassen möchten, dass er auf eine oder mehrere der folgenden Arten reagiert:

- Nehmen Sie an Build, Bereitstellung, Konfigurationen und Quell Code Verwaltung Teil.

- Bietet Debugunterstützung.

- Zeigen Sie Projekt Elemente in **Projektmappen-Explorer**an.

- Verwenden Sie das Dialogfeld **Projekt öffnen** oder **Neues Projekt** .

- Unterstützung der Projekt Schachtelung

## <a name="extend-an-existing-project-type"></a>Erweitern eines vorhandenen Projekt Typs
 Möglicherweise möchten Sie einen neuen Projekttyp erstellen, der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] auf folgende Weise verwenden kann, um das Verhalten eines vorhandenen Projekt Typs zu ändern oder zu erweitern, z. b. zum Ändern des Buildprozesses für [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekte:

- Arbeiten Sie mit mehreren Dateien als einzelne Einheit.

- Zeigt eine einzelne Datei als Hierarchie von unter Elementen an.

- Anzeigen eines Befehls Kontexts um Editoren.

- Zeigen Sie einen Dienst Kontext für Editoren an.

## <a name="use-an-existing-project-type"></a>Vorhandenen Projekttyp verwenden
 Das Erstellen eines neuen Projekts ist manchmal nicht erforderlich. In der folgenden Tabelle sind die Tasks aufgeführt, für die Sie keinen Projekttyp erstellen müssen.

|Aufgabe|Beschreibung|
|----------|-----------------|
|Verarbeiten von Befehlen|Alle VSPackage können Befehle verarbeiten.|
|Aufbauen eines Editors|Benutzerdefinierte Editoren können registriert werden. Weitere Informationen finden Sie unter [Dokument Fenster und Editoren](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc).|
|Besitzende Fenster|Sie können sowohl Tool-als auch Dokument Fenster erstellen, ohne einen neuen Projekttyp hinzuzufügen.|
|Verfügbar machen von Eigenschaften im Eigenschaftenfenster|Alle-Objekte können Eigenschaften verfügbar machen.|

## <a name="create-a-project-subtype"></a>Erstellen eines Projekt unter Typs
 Mithilfe von Projekt Untertypen können Sie einen verwalteten Projekttyp erweitern, ohne einen neuen Projekttyp erstellen zu müssen. Projekt Untertypen verwenden com-Aggregation, um verwaltete Projekte zu erweitern, die in Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] oder [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] geschrieben wurden. Mit com-Aggregation können Sie einen Großteil der Implementierung des verwalteten Projekt Systems wieder verwenden und dennoch für ein bestimmtes Szenario durch Aggregation und die Verwendung von unterstützenden Schnittstellen anpassen. Weitere Informationen zu Projekt Untertypen finden Sie unter [Projekt Untertypen](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Siehe auch
- [Dokument Fenster und-Editoren](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)