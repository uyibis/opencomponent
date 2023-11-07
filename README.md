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

The Gallery component is a media manager that consumes the File Uploader component. It allows users to reuse their previously uploaded media files.

### Progress Bar

The Progress Bar component is a visual indicator for tasks or processes with progress updates, providing a better user experience.

### Presenter

The Presenter component is perfect for presenting content or images with a smooth transition between slides. It's ideal for showcasing content in a dynamic and engaging manner.

## Installation

Clone the repository into your project's JavaScript folder and use the components directly in your project.

### Loader

The Loader component provides a visually appealing loading indicator to keep your users engaged while data is being fetched or processed.

**GitHub Repository**: [View on GitHub](https://github.com/uyibis/opencomponent/tree/master/loader)

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

### File Uploader

The File Uploader component simplifies the process of uploading files and supports various file types and configurations.

**GitHub Repository**: [View on GitHub](https://github.com/uyibis/opencomponent/tree/master/file_upload)

| Property     | Type     | Description                                          |
| ------------ | -------- | ---------------------------------------------------- |
| `url`        | String   | The URL for uploading files.                        |

**Emitted Events:**

- `file-uploaded`: Emitted when a file is successfully uploaded.

### Gallery Dialog

The Gallery Dialog component is a media manager that allows users to select and manage images and videos from their previously uploaded media files.

**GitHub Repository**: [View on GitHub](https://github.com/uyibis/opencomponent/tree/master/gallery_dialog)

| Property     | Type     | Description                                          |
| ------------ | -------- | ---------------------------------------------------- |
| `uploader_url` | String | The URL for uploading files.                       |
| `gallery_url`  | String | The URL for fetching gallery images.                |
| `event_chanel` | String | The event name for emitting selected images.        |

**Emitted Events:**

- `gallery-selected`: Emitted when selected images are applied.


## License

This project is licensed under the terms of the MIT License.

### MIT License

[MIT License Text]

