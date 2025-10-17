# VideoDB n8n Workflows

This repository contains a collection of n8n workflows that demonstrate how to integrate [VideoDB](https://videodb.io) with various services to automate video processing and analysis tasks. These workflows are designed to be modular and can be adapted to fit your specific needs.

## Workflows

This repository includes the following workflows:

### Master Meeting Workflow

**Goal:**

This workflow automates the complete meeting lifecycle from recording to analysis and distribution. It processes different meeting types (Sync, Planning, Interview, Sales) and distributes insights to Slack, Coda, and HubSpot based on the meeting context.

The workflow handles different meeting types with intelligent branching instead of requiring separate workflows for each type.

**Prerequisites:**

1.  N8N Instance: Running N8N automation platform (cloud or self-hosted)
2.  VideoDB API Key: Obtain from VideoDB Console
3.  VideoDB N8N Node: Install the custom node in your N8N instance
4.  Meeting Platform: Platform with bot recording support (Zoom, Teams, Google Meet)
5.  Slack Workspace: With bot permissions for notifications
6.  Coda Workspace: With API token for meeting documentation
7.  HubSpot Account: With API key for sales meeting integration

**Main Workflow Steps:**

**Step 1: Meeting Recording**
1.  Form trigger collects meeting URL and meeting type (Sync/Planning/Interview/Sales)
2.  VideoDB joins the meeting and records the session
3.  Wait for meeting completion before processing

**Step 2: Video Processing**
1.  Index spoken words from the recorded meeting
2.  Generate transcript with speaker identification and mapping
3.  Process video content for analysis readiness

**Step 3: AI Analysis with Branching**
1.  Switch workflow based on meeting type selection
2.  Apply custom AI prompts for each meeting type:
    -   **Planning**: Extract strategic outcomes, decisions, and action items
    -   **Interview**: Generate candidate evaluation with recommendation
    -   **Sales**: Identify deal details, stage, amount, and next steps
    -   **Sync**: Create summaries with follow-ups and task assignments

**Step 4: Multi-Platform Distribution**
1.  Send formatted updates to Slack channels
2.  Update Coda databases with meeting insights
3.  For sales meetings: Create or update HubSpot deal records
4.  Route data to appropriate platforms based on meeting type

**Conclusion:**

This workflow consolidates multiple meeting types into one automated system, ensuring consistent documentation and appropriate distribution across your business tools.

---

### Interview Evaluation Workflow

**Goal:**

This workflow converts interview recordings into structured candidate evaluations with assessments and recommendations. It standardizes the interview evaluation process and distributes results to both Coda and Slack for hiring team collaboration.

The workflow ensures consistent evaluation criteria across all interviews, making candidate comparison more objective.

**Prerequisites:**

1.  N8N Instance: Running N8N automation platform (cloud or self-hosted)
2.  VideoDB API Key: Obtain from VideoDB Console
3.  VideoDB N8N Node: Install the custom node in your N8N instance
4.  Meeting Platform: Platform with bot recording capability for interviews
5.  Coda Workspace: For candidate tracking and evaluation storage
6.  Slack Workspace: For hiring team notifications

**Main Workflow Steps:**

**Step 1: Interview Recording**
1.  Form trigger collects meeting URL for the interview session
2.  VideoDB joins the interview and records the session
3.  Wait for interview completion before processing

**Step 2: Video Processing**
1.  Index spoken words from the interview recording
2.  Generate transcript with speaker identification (interviewer vs candidate)
3.  Prepare audio content for AI analysis

**Step 3: AI Evaluation**
1.  Extract structured candidate information:
    -   Candidate name and background details
    -   Role they're applying for
    -   Personality and communication assessment
2.  Generate hiring recommendation (Strongly Recommended/Recommended/Consider with Reservations/Not Recommended)
3.  Evaluate key strengths, areas for development, and cultural fit (High/Medium/Low)

**Step 4: Results Distribution**
1.  Add candidate evaluation to Coda hiring database with structured fields
2.  Send formatted evaluation summary to Slack hiring team channels
3.  Ensure consistent format for easy candidate comparison

**Conclusion:**

This workflow provides hiring teams with standardized candidate evaluations distributed across both documentation (Coda) and communication (Slack) platforms for comprehensive hiring decision support.

---

### Meeting Summary Workflow

**Goal:**

This workflow converts recorded meetings into structured summaries with action items and key decisions. It serves as a universal meeting processor for general business meetings and distributes summaries to both Coda and Slack.

The workflow ensures consistent meeting documentation and team notification for any type of business meeting.

**Prerequisites:**

1.  N8N Instance: Running N8N automation platform (cloud or self-hosted)
2.  VideoDB API Key: Obtain from VideoDB Console
3.  VideoDB N8N Node: Install the custom node in your N8N instance
4.  Meeting Recording: Access to meeting recording (any platform with recording capability)
5.  Coda Workspace: For meeting documentation storage
6.  Slack Workspace: For team notifications

**Main Workflow Steps:**

**Step 1: Meeting Recording**
1.  Process recorded meeting files or live meeting recordings
2.  Initiate VideoDB processing for the meeting content
3.  Wait for recording completion before analysis

**Step 2: Video Processing**
1.  Index spoken words and generate comprehensive transcript
2.  Create timestamped transcript for reference
3.  Prepare content for AI summarization

**Step 3: AI Summarization**
1.  Extract meeting title and purpose
2.  Identify key discussion points and decisions made
3.  Extract action items with ownership assignments and due dates
4.  Structure information into consistent format

**Step 4: Documentation and Distribution**
1.  Create new entry in Coda project database with structured fields:
    -   Date and meeting metadata
    -   Executive summary
    -   Action points with assignments
    -   Decision log
2.  Send formatted meeting summary to Slack with action item notifications

**Conclusion:**

This workflow creates a complete meeting documentation system that stores structured summaries in Coda while keeping teams informed through Slack notifications.

---

### Sales Meeting to HubSpot Workflow

**Goal:**

This workflow captures sales conversations and syncs deal information directly to HubSpot CRM. It eliminates manual data entry by extracting key deal details from sales calls and updating CRM records automatically.

The workflow ensures consistent CRM data entry and prevents missed sales opportunities through automated deal tracking.

**Prerequisites:**

1.  N8N Instance: Running N8N automation platform (cloud or self-hosted)
2.  VideoDB API Key: Obtain from VideoDB Console
3.  VideoDB N8N Node: Install the custom node in your N8N instance
4.  HubSpot CRM: With API access for deal and contact management
5.  Meeting Recording: Capability for sales call recording
6.  HubSpot Pipeline: Configured deal pipeline with appropriate stages

**Main Workflow Steps:**

**Step 1: Sales Call Recording**
1.  Record sales conversations automatically
2.  Ensure complete call capture before processing
3.  Verify audio quality for accurate transcript generation

**Step 2: Video Processing**
1.  Index spoken words from sales call audio
2.  Generate detailed transcript of the conversation
3.  Prepare content for deal analysis

**Step 3: Deal Intelligence Extraction**
1.  Extract company/prospect name for deal identification
2.  Assess current deal stage based on conversation content
3.  Identify deal value and monetary discussions
4.  Extract next steps and follow-up requirements
5.  Categorize deals into appropriate HubSpot pipeline stages

**Step 4: HubSpot CRM Integration**
1.  Create new deal records or update existing ones
2.  Populate CRM fields with:
    -   Deal name and estimated value
    -   Current pipeline stage
    -   Meeting summary and discussion points
    -   Next steps and follow-up tasks
3.  Log meeting as activity in deal timeline

**Conclusion:**

This workflow maintains accurate, up-to-date CRM data by automatically capturing and structuring sales conversation details in HubSpot, supporting consistent deal tracking and sales process management.

---

### YouTube Video to Notion Workflow

**Goal:**

This workflow monitors YouTube channels for new content and automatically creates summaries in Notion. It builds a searchable knowledge base of video content without requiring manual video watching.

The workflow helps teams track multiple content sources and extract insights from educational or industry content automatically.

**Prerequisites:**

1.  N8N Instance: Running N8N automation platform (cloud or self-hosted)
2.  VideoDB API Key: Obtain from VideoDB Console
3.  VideoDB N8N Node: Install the custom node in your N8N instance
4.  Notion Workspace: With page/database access for content storage
5.  YouTube Channels: Specific channels to monitor via RSS feed
6.  RSS Configuration: N8N RSS trigger setup for channel monitoring

**Main Workflow Steps:**

**Step 1: Content Discovery**
1.  RSS feed trigger monitors specified YouTube channels for new uploads
2.  Capture video metadata (title, description, author, publication date, URL)
3.  Activate immediately when new video is published

**Step 2: Video Upload and Processing**
1.  Upload video content to VideoDB for processing
2.  Monitor upload and indexing completion status
3.  Index spoken words for transcript extraction

**Step 3: Content Analysis**
1.  Generate full transcript of video content with timestamps
2.  Apply AI summarization to extract:
    -   Key topics and themes discussed
    -   Important quotes and insights
    -   Technical concepts explained
    -   Action items or recommendations mentioned

**Step 4: Notion Integration**
1.  Create new Notion page with structured video summary
2.  Include comprehensive documentation:
    -   Video title and source channel information
    -   Publication date and metadata
    -   Detailed summary with key insights
    -   Direct link to original video
3.  Add entry to Notion database with appropriate tags for searching

**Conclusion:**

This workflow automates video content monitoring and creates a searchable knowledge repository in Notion, enabling teams to stay informed about relevant content without manual video consumption.

---

### Video Dubbing to Google Drive Workflow

**Goal:**

This workflow takes video URLs, uploads them to VideoDB, dubs them into different languages, and saves the dubbed videos to Google Drive. It enables automatic video localization for global content distribution.

The workflow is useful for content creators who need to create multilingual versions of their videos for international audiences without manual dubbing processes.

**Prerequisites:**

1.  N8N Instance: Running N8N automation platform (cloud or self-hosted)
2.  VideoDB API Key: Obtain from VideoDB Console
3.  VideoDB N8N Node: Install the custom node in your N8N instance
4.  Google Drive Account: With API access for file uploads
5.  Video URLs: Access to video content that needs dubbing

**Main Workflow Steps:**

**Step 1: Video Input and Upload**
1.  Form trigger collects YouTube video URL for dubbing
2.  Upload video content to VideoDB for processing
3.  Wait for upload completion before proceeding

**Step 2: Video Processing**
1.  Monitor upload status via HTTP request polling
2.  Verify video upload is complete
3.  Prepare video for dubbing operations

**Step 3: Video Dubbing**
1.  Use VideoDB dubbing operation to create dubbed version
2.  Process video with target language dubbing
3.  Monitor dubbing completion status

**Step 4: Google Drive Storage**
1.  Download dubbed video from VideoDB
2.  Upload dubbed video to Google Drive folder
3.  Store video with appropriate naming for language identification

**Conclusion:**

This workflow automates video dubbing and storage, enabling easy creation of multilingual video content that can be distributed through Google Drive or integrated into other workflows.

---

### Video Subtitle to Google Drive Workflow

**Goal:**

This workflow takes video URLs, uploads them to VideoDB, indexes spoken content, adds subtitle overlays directly to the video, and saves the subtitled videos to Google Drive. It creates professional subtitle overlays that are permanently embedded in the video.

The workflow is useful for creating accessible video content with professional subtitle styling that works across all platforms, unlike platform-specific auto-generated subtitles.

**Prerequisites:**

1.  N8N Instance: Running N8N automation platform (cloud or self-hosted)
2.  VideoDB API Key: Obtain from VideoDB Console
3.  VideoDB N8N Node: Install the custom node in your N8N instance
4.  Google Drive Account: With API access for file uploads
5.  Video URLs: Access to video content that needs subtitles

**Main Workflow Steps:**

**Step 1: Video Input and Upload**
1.  Form trigger collects YouTube video URL for subtitle processing
2.  Upload video content to VideoDB for processing
3.  Wait for upload completion before proceeding

**Step 2: Spoken Content Indexing**
1.  Monitor upload status via HTTP request polling
2.  Index spoken words from the video content
3.  Generate timestamped transcript for subtitle creation

**Step 3: Subtitle Generation and Overlay**
1.  Use VideoDB subtitle operation to add subtitle overlays
2.  Create professional subtitle styling embedded in video
3.  Process video with precisely timed subtitle overlays

**Step 4: Google Drive Storage**
1.  Download subtitled video from VideoDB
2.  Upload subtitled video to Google Drive folder
3.  Store video with subtitles permanently embedded

**Conclusion:**

This workflow creates professional subtitled videos with embedded subtitle overlays, making content accessible across all platforms while maintaining consistent subtitle styling and timing.

## Getting Started

To use these workflows, you will need to have an n8n instance running and have the VideoDB n8n node installed. You will also need to have API keys for the services you want to integrate with.

Once you have everything set up, you can import the JSON files into your n8n instance and configure the credentials for each node.

## Contributing

We welcome contributions to this repository. If you have a workflow that you would like to share, please open a pull request.