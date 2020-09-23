# Kotlin 1.4.10 Linker Bug Repro Project

This project triggers a crash when linking the iOS framework in RELEASE mode.

Run `./gradlew clean linkReleaseFrameworkIosArm64` or `./gradlew clean linkReleaseFrameworkIosX64` to trigger the following exception:
```
e: java.lang.Error: Invalid module
        at org.jetbrains.kotlin.backend.konan.llvm.IrToBitcodeKt.verifyModule(IrToBitcode.kt:85)
        at org.jetbrains.kotlin.backend.konan.llvm.IrToBitcodeKt.verifyModule$default(IrToBitcode.kt:75)
        at org.jetbrains.kotlin.backend.konan.Context.verifyBitCode(Context.kt:364)
        at org.jetbrains.kotlin.backend.konan.llvm.BitcodePhasesKt$verifyBitcodePhase$1.invoke(BitcodePhases.kt:298)
        at org.jetbrains.kotlin.backend.konan.llvm.BitcodePhasesKt$verifyBitcodePhase$1.invoke(BitcodePhases.kt)
        at org.jetbrains.kotlin.backend.konan.KonanLoweringPhasesKt$makeKonanModuleOpPhase$1.invoke(KonanLoweringPhases.kt:61)
        at org.jetbrains.kotlin.backend.konan.KonanLoweringPhasesKt$makeKonanModuleOpPhase$1.invoke(KonanLoweringPhases.kt:59)
        at org.jetbrains.kotlin.backend.common.phaser.AbstractNamedPhaseWrapper$runBody$1.invoke(CompilerPhase.kt:128)
        at org.jetbrains.kotlin.backend.common.phaser.CompilerPhaseKt.downlevel(CompilerPhase.kt:24)
        at org.jetbrains.kotlin.backend.common.phaser.AbstractNamedPhaseWrapper.runBody(CompilerPhase.kt:127)
        at org.jetbrains.kotlin.backend.common.phaser.AbstractNamedPhaseWrapper.invoke(CompilerPhase.kt:105)
        at org.jetbrains.kotlin.backend.common.phaser.CompositePhase.invoke(PhaseBuilders.kt:30)
        at org.jetbrains.kotlin.backend.common.phaser.AbstractNamedPhaseWrapper$runBody$1.invoke(CompilerPhase.kt:128)
        at org.jetbrains.kotlin.backend.common.phaser.CompilerPhaseKt.downlevel(CompilerPhase.kt:24)
        at org.jetbrains.kotlin.backend.common.phaser.AbstractNamedPhaseWrapper.runBody(CompilerPhase.kt:127)
        at org.jetbrains.kotlin.backend.common.phaser.AbstractNamedPhaseWrapper.invoke(CompilerPhase.kt:105)
        at org.jetbrains.kotlin.backend.common.phaser.CompositePhase.invoke(PhaseBuilders.kt:23)
        at org.jetbrains.kotlin.backend.common.phaser.AbstractNamedPhaseWrapper$runBody$1.invoke(CompilerPhase.kt:128)
        at org.jetbrains.kotlin.backend.common.phaser.CompilerPhaseKt.downlevel(CompilerPhase.kt:24)
        at org.jetbrains.kotlin.backend.common.phaser.AbstractNamedPhaseWrapper.runBody(CompilerPhase.kt:127)
        at org.jetbrains.kotlin.backend.common.phaser.AbstractNamedPhaseWrapper.invoke(CompilerPhase.kt:105)
        at org.jetbrains.kotlin.backend.common.phaser.CompositePhase.invoke(PhaseBuilders.kt:30)
        at org.jetbrains.kotlin.backend.common.phaser.AbstractNamedPhaseWrapper$runBody$1.invoke(CompilerPhase.kt:128)
        at org.jetbrains.kotlin.backend.common.phaser.CompilerPhaseKt.downlevel(CompilerPhase.kt:24)
        at org.jetbrains.kotlin.backend.common.phaser.AbstractNamedPhaseWrapper.runBody(CompilerPhase.kt:127)
        at org.jetbrains.kotlin.backend.common.phaser.AbstractNamedPhaseWrapper.invoke(CompilerPhase.kt:105)
        at org.jetbrains.kotlin.backend.common.phaser.CompilerPhaseKt.invokeToplevel(CompilerPhase.kt:42)
        at org.jetbrains.kotlin.backend.konan.KonanDriverKt.runTopLevelPhases(KonanDriver.kt:28)
        ...
```