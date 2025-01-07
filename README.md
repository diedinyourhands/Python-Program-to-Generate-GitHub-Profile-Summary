def format_github_profile(name, bio, skills, projects):
    profile_template = f"""
    # {name}'s GitHub Profile

    ## Bio
    {bio}

    ## Skills
    - {', '.join(skills)}

    ## Projects
    """
    for project in projects:
        profile_template += f"""
        ### {project['title']}
        - **Description:** {project['description']}
        - **Technologies:** {project['technologies']}
        - **Link:** [View Project]({project['link']})
        """
    
    return profile_template.strip()

def main():
    print("Enter your GitHub profile details:")
    
    name = input("Your Name: ")
    bio = input("A brief bio about yourself: ")

    skills = input("Enter your skills (comma-separated): ").split(',')
    skills = [skill.strip() for skill in skills]  # Clean up whitespace

    projects = []
    while True:
        print("\nEnter your project details (or type 'done' to finish):")
        title = input("Project Title (or 'done'): ")
        if title.lower() == 'done':
            break
        description = input("Project Description: ")
        technologies = input("Technologies Used (comma-separated): ")
        link = input("Project Link: ")

        projects.append({
            'title': title,
            'description': description,
            'technologies': technologies,
            'link': link
        })

    formatted_profile = format_github_profile(name, bio, skills, projects)
    
    print("\nYour GitHub Profile Summary:")
    print(formatted_profile)

if __name__ == "__main__":
    main()
