# open-component

"open-component" is a collection of Vue 3 components designed to enhance your web application with various UI elements and functionalities. These components provide easy integration and customization to improve user experiences and reduce development time.

## Table of Contents

- [Components](#components)
    - [Loader](#loader)
    - [File Uploader](#file-uploader)
    - [Gallery](#gallery)
    - [Progress Bar](#progress-bar)
    - [Presenter](#presenter)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Components

### Loader

The Loader component provides a visually appealing loading indicator to keep your users engaged while data is being fetched or processed.

### File Uploader

The File Uploader component simplifies the process of uploading files and supports various file types and configurations.

### Gallery

The Gallery component is a media manager that consume the file uploader component. Its allow user to re-use their previous uploaded media file
### Progress Bar

The Progress Bar component is a visual indicator for tasks or processes with progress updates, providing a better user experience.

### Presenter

The Presenter component is perfect for presenting content or images with a smooth transition between slides. It's ideal for showcasing content in a dynamic and engaging manner.

## Installation

clone repo into your js folder of your project and use the component directly in your project


### `Loader` Vue Component

| Property     | Type     | Description                                          |
| ------------ | -------- | ---------------------------------------------------- |
| `loading`    | Boolean  | Determines whether the loading indicator is shown. |

**Emitted Events:**

None

### `presenter_table_content` Vue Component

| Property     | Type     | Description                                          |
| ------------ | -------- | ---------------------------------------------------- |
| `procedures` | Array    | Array of procedures and their associated illustrations for the slides.

**Emitted Events:**

None

### `Progress` Vue Component

| Property     | Type     | Description                                          |
| ------------ | -------- | ---------------------------------------------------- |
| `progress`   | Number   | Completion progress value, between 0 and 100.      |

**Emitted Events:**

None

### `FileUploader` Vue Component

| Property     | Type     | Description                                          |
| ------------ | -------- | ---------------------------------------------------- |
| `url`        | String   | The URL for uploading files.                        |

**Emitted Events:**

- `file-uploaded`: Emitted when a file is successfully uploaded.

### `Gallery` Vue Component

| Property     | Type     | Description                                          |
| ------------ | -------- | ---------------------------------------------------- |
| `uploader_url` | String | The URL for uploading files.                       |
| `gallery_url`  | String | The URL for fetching gallery images.                |
| `event_chanel` | String | The event name for emitting selected images.        |

**Emitted Events:**

[//]: # (- `file-uploaded`: Emitted when a file is successfully uploaded.)
- `gallery-selected`: Emitted when selected images are applied.

This project is licensed under the terms of the MIT License.

### MIT License