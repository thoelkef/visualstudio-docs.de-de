---
title: Dia2dump-Beispiel | Microsoft-Dokumentation
ms.date: 07/24/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a91b12ae49028d2c84c8308d043d69bf2297797
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54939115"
---
# <a name="dia2dump-sample"></a>Dia2dump-Beispiel

Dia2dump-Beispiel veranschaulicht die Microsoft Debuggen Schnittstelle Access Software Development Kit (DIA-SDK) zu verwenden, um eine PDB-Datei Informationen abzufragen.

Dia2dump-Beispiel wird mit Visual Studio installiert und enthält die Projektmappe und Quelldateien. Die kompilierte ausführbare Datei, die von der Befehlszeile aus ausgeführt wird. Sie können den Inhalt der eine gesamte Programmdatenbankdatei (.pdb) anzeigen, oder nur in den Abschnitten interessiert.

## <a name="install-the-sample"></a>Installieren des Beispiels

Das Beispiel installiert ist, bei der Auswahl der **Desktopentwicklung mit C++** Workload im Visual Studio-Installer. Informationen zum Installieren von Visual Studio, und wählen Sie bestimmte arbeitsauslastungen und einzelnen Komponenten finden Sie unter [Installieren von Visual Studio](../../install/install-visual-studio.md).

Bei der Installation ist das Beispiel, in Ihrem Visual Studio-Installationsverzeichnis, in ein Unterverzeichnis namens \DIA SDK\Samples\DIA2Dump.

## <a name="build-the-sample"></a>Erstellen des Beispiels

Standardmäßig ist das Installationsverzeichnis ein geschütztes Verzeichnis. Das bedeutet, dass es sich bei Verwendung einer Developer-Eingabeaufforderung mit erhöhten Rechten oder eine Instanz von Visual Studio zum Erstellen und bearbeiten die beispiellösung an diesem Speicherort. Um den Build zu vereinfachen, empfehlen wir, Sie kopieren Sie die Dateien zuerst im Beispielverzeichnis aus, um ein anderes Verzeichnis, z. B. einen Ordner im Ordner "Dokumente", und klicken Sie dann das Beispiel erstellen.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>So erstellen Sie die Dia2Dump-Beispiel in Visual Studio

1. Öffnen Sie die Datei DIA2Dump.sln in Visual Studio. Wenn Sie die Lösung nicht in ein anderes Verzeichnis kopiert haben, werden Sie möglicherweise aufgefordert, Visual Studio mit erweiterten Berechtigungen neu zu starten.

1. In **Projektmappen-Explorer**, wählen Sie das Dia2Dump-Projekt (nicht auf die Projektmappe).

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Ausführliche Informationen finden Sie unter [Working with Project Properties (Arbeiten mit Projekteigenschaften)](/cpp/ide/working-with-project-properties).

1. Öffnen der **Konfigurationseigenschaften** > **C/C++-** > **allgemeine** Eigenschaftenseite.

1. In der **Additional Include Directories** -Eigenschaft, wählen Sie im Dropdown-Steuerelement, und wählen Sie dann **bearbeiten**.

1. In der **Additional Include Directories** Dialogfeldecke, in das Bearbeitungsfeld, geben Sie die `$(VSInstallDir)DIA SDK\include` Verzeichnis. Fügen Sie diesem Verzeichnis aus, um sicherzustellen, dass der Compiler die Datei dia2.h finden kann. Klicken Sie auf **OK**, um die Änderungen zu speichern.

1. Wählen Sie **OK** zum Speichern der Änderungen in den Projekteigenschaften.

1. Auf der **erstellen** Menü wählen **Projektmappe neu erstellen**. Standardmäßig erstellt Visual Studio eine Debugversion des Beispiels, befindet sich in einem Debug-Unterverzeichnis des Verzeichnisses Lösung.

1. Schließen Sie Visual Studio.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>So erstellen Sie die Dia2Dump-Beispiel in der Befehlszeile

1. Ändern Sie in einem Developer-Eingabeaufforderungsfenster in das Verzeichnis, in dem Sie die Beispieldateien kopiert. Wenn Sie das Beispiel in ein anderes Verzeichnis kopieren nicht, können Sie mit einer mit erhöhten Rechten (als Administrator ausführen) Developer-Eingabeaufforderungsfenster.

1. Geben Sie den Befehl `nmake makefile` die standardmäßigen Debugkonfiguration von dia2dump.exe zu erstellen.

## <a name="run-the-dia2dump-sample"></a>Führen Sie das Dia2Dump-Beispiel

Dia2Dump.exe abhängig von der Msdia*Version*DLL-COM-Server, seine Dienste bereitstellen. In Visual Studio 2015 und Visual Studio 2017 ist die Version "msdia140.dll". Wenn die Msdia*Version*DLL-COM-Server nicht initialisiert wird, müssen Sie ihn registrieren, bevor dia2dump.exe arbeiten können. Das DIA-SDK-Verzeichnis wurde ein Unterverzeichnis "Bin", die die X86 enthält Version der DLL. Eine Version für X64 Architektur Computer bin\amd64 wird und eine Version für ARM ist in Bin\arm. Um die Dll registrieren möchten, öffnen Sie ein Eingabeaufforderungsfenster mit erhöhten Rechten Entwickler, und wechseln Sie zum Verzeichnis mit der Version für Ihre Architektur. Geben Sie den Befehl `regsvr32 msdia140.dll` COM-Server zu registrieren.

### <a name="to-run-the-sample"></a>So führen Sie das Beispiel aus

1. Öffnen Sie eine Eingabeaufforderung, und wechseln Sie zum Verzeichnis, das die dia2dump.exe enthält, die Sie erstellt.

1. Geben Sie den Befehl `dia2dump filename` , in denen *Filename* ist der Name des eine PDB-Datei, um zu überprüfen. Wenn die PDB-Datei in einem anderen Verzeichnis ist, verwenden Sie den vollständigen Pfad zu der Datei als *Filename*. Dieser Befehl listet alle Daten in die PDB-Datei.

1. Dia2Dump verfügt über weitere Optionen, um nur ausgewählte Informationen anzuzeigen. Verwenden der `dia2dump -?` Befehl aus, um alle verfügbaren Optionen aufgelistet.

## <a name="see-also"></a>Siehe auch

- [Übertragung, Migration und Upgrade der Visual Studio-Projekte](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)  
