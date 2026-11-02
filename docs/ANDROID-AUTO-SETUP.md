# Android Auto setup

This document describes the remaining work needed to turn the MuseAndroidAuto starter scaffold into a shippable Android Auto experience.

## Current repository state

This checkout does not contain a complete Android Studio project or runnable Android Auto service. `MuseAndroidAuto/` currently contains only app-icon metadata; the static `site/` is the runnable demo.

## Requirements

- Android Studio with a compatible Android SDK and build tools
- An Android application ID, signing configuration, and a test device or emulator
- Android Auto Desktop Head Unit (DHU) or an Android phone connected to a compatible vehicle
- A backend endpoint and credentials for chat, places, reservations, and speech services

## Create the Android project

1. Create or restore the Android Studio project and set its package/application ID.
2. Add the required Gradle modules, manifest metadata, resources, and Kotlin/Java source files.
3. Keep signing keys, service credentials, and local configuration out of source control.

## Enable Android Auto support

Choose the Android Auto integration that matches the product experience. For a templated in-car experience, configure the Android for Cars App Library, the required manifest metadata, the supported app category, and the appropriate service entry point. Follow Google's current Android Auto and Android for Cars guidance for category eligibility and review requirements.

## Wire the application

The checked-in project is intentionally minimal. Before building, add the Android source files, resource files, manifest entries, service implementation, and test files to the appropriate Gradle modules. Add only the libraries required by the implementation, such as the Android for Cars App Library, speech/audio components, networking, and secure credential storage.

## Configure services

Replace service stubs with production implementations and provide authenticated endpoints for:

- Chat responses
- Place search and details
- Reservation lookup and creation
- Speech recognition and synthesis

Use secure runtime configuration. Do not commit tokens or private keys.

## Test

1. Build the Android application and run its unit and instrumentation tests.
2. Launch Android Auto Desktop Head Unit or connect a development phone to a compatible vehicle.
3. Verify template navigation, voice permissions, audio interruption handling, network failures, and reservation confirmation flows.
4. Test user-facing actions while stationary and follow Google's Android Auto quality and distraction-optimized design requirements.

## App icon

When the Android project is restored, add the production app icon to the appropriate Android `mipmap` resources. The existing `MuseAndroidAuto/` directory contains only legacy icon metadata from the starter scaffold; it is not a complete Android resource set.

## Website deployment

The Pages workflow expects a `site/` directory. The starter pages in this repository are self-contained static files and can be deployed by the existing workflow once its repository and Pages settings are configured.
