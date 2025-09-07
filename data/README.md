# Task Management System Sample Data

This folder contains realistic sample data for the Task Management System template:

## Collaborative Task Management Structure

```
data/
├── project/           # 15 projects for organization
│   ├── [uuid].json    # Individual project files
│   └── relation.json  # Project relationships
├── task/              # 60 tasks with assignments
│   ├── [uuid].json    # Individual task files
│   └── relation.json  # Task relationships
├── team_member/       # 15 team members
│   ├── [uuid].json    # Individual member files
│   └── relation.json  # Member relationships
└── comment/           # 50 task comments
    ├── [uuid].json    # Individual comment files
    └── relation.json  # Comment relationships
```

## Sample Data Features

### Projects (15 records)
- Complete project profiles with timelines
- Priority levels and status tracking
- Start/end dates and color coding
- Team assignment and management
- Progress monitoring capabilities

### Tasks (60 records)
- Individual work items and activities
- Priority levels: Low, Medium, High, Critical
- Status tracking: Todo, In Progress, Review, Done, Cancelled
- Due date management and time estimation
- Assignment to team members
- Tag-based organization and filtering
- Creation and completion timestamps

### Team Members (15 records)
- Complete user profiles with skills and roles
- Bio information and avatar support
- Join date and status tracking
- Email contacts and role assignments
- Task assignment capabilities

### Comments (50 records)
- Task-based discussion and collaboration
- Author attribution and timestamps
- Status tracking for comment moderation
- Internal team communication flags
- Thread-based task conversations

## Relationship Format

### Project Relations
```json
{
  "project-uuid": {
    "task": {
      "relation_type": "has_many",
      "ids": ["task-uuid-1", "task-uuid-2"]
    },
    "team_member": {
      "relation_type": "has_many",
      "ids": ["member-uuid-1", "member-uuid-2"]
    }
  }
}
```

### Task Relations
```json
{
  "task-uuid": {
    "project": {
      "relation_type": "has_one",
      "id": "project-uuid"
    },
    "team_member": {
      "relation_type": "has_one",
      "id": "member-uuid"          // Task assignment
    },
    "comment": {
      "relation_type": "has_many",
      "ids": ["comment-uuid-1", "comment-uuid-2"]
    }
  }
}
```

### Comment Relations
```json
{
  "comment-uuid": {
    "task": {
      "relation_type": "has_one",
      "id": "task-uuid"
    },
    "team_member": {
      "relation_type": "has_one",
      "id": "member-uuid"          // Comment author
    }
  }
}
```

## Team Collaboration Patterns

### Project Workflows
- Multiple projects with different priorities
- Task breakdown and assignment
- Progress tracking and status updates
- Team member allocation across projects

### Task Management
- Comprehensive task lifecycle management
- Priority-based task organization
- Due date tracking and deadline management
- Team assignment and responsibility tracking
- Comment-based collaboration on tasks

### Team Coordination
- Role-based team member management
- Skill tracking and team composition
- Task assignment based on capabilities
- Collaborative commenting and feedback

## Sample Workflows

### Development Project Example
- **Project**: Mobile App Development
- **Tasks**: UI Design, Backend API, Testing, Deployment
- **Team**: Designer, Developer, QA Engineer, DevOps
- **Comments**: Design feedback, code reviews, bug reports

### Marketing Campaign Example
- **Project**: Product Launch Campaign
- **Tasks**: Market Research, Content Creation, Social Media, Analytics
- **Team**: Marketing Manager, Content Writer, Social Media Specialist, Analyst
- **Comments**: Campaign feedback, performance discussions

### Content Creation Example
- **Project**: Blog Content Strategy
- **Tasks**: Topic Research, Writing, Editing, Publishing, SEO
- **Team**: Content Manager, Writers, Editor, SEO Specialist
- **Comments**: Editorial feedback, SEO suggestions

## Data Generation

This collaborative data was generated using the Apito Data Generator:

```bash
# Regenerate data
./apito-gen
```

## Statistics

- **Total Files**: 144
- **Projects**: 15 with comprehensive project management
- **Tasks**: 60 with complete task lifecycle data
- **Team Members**: 15 user profiles with skills and roles
- **Comments**: 50 discussion threads on tasks
- **Relationships**: 100% coverage with proper assignments
- **UUID Format**: All files use UUID v4 naming
- **Collaboration Features**: Complete comment threading and team assignment

## Import Instructions

### Via Apito Dashboard
1. Create new general project in Apito Dashboard
2. Import schema.json for task management structure
3. Upload data folder maintaining relationship structure
4. Configure team access and project workflows

### Via Apito CLI
```bash
apito import schema.json
apito import data/ --preserve-structure
```

## Use Cases Demonstrated

- **Agile Project Management**: Sprint-based development workflows
- **Team Task Tracking**: Individual and team task management
- **Collaborative Work**: Comment-based team communication
- **Project Portfolio**: Multiple project management
- **Resource Management**: Team member skill tracking and assignment
- **Progress Monitoring**: Status tracking and completion management

## Task Lifecycle Examples

### Software Development Task
- **Title**: "Implement user authentication API"
- **Priority**: High
- **Status**: In Progress
- **Assigned**: Backend Developer
- **Comments**: Technical discussions, code review feedback

### Design Task
- **Title**: "Create mobile app wireframes"
- **Priority**: Medium
- **Status**: Review
- **Assigned**: UI/UX Designer
- **Comments**: Design feedback, revision requests

### Marketing Task
- **Title**: "Write product launch blog post"
- **Priority**: Low
- **Status**: Todo
- **Assigned**: Content Writer
- **Comments**: Content guidelines, SEO requirements

---

**Note**: This demonstrates comprehensive task management patterns with project organization, team collaboration, and comment-based communication suitable for software development, marketing, content creation, and general project management scenarios.
