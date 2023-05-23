---
# Leave the homepage title empty to use the site title
title: 
date: 2022-10-24
type: landing

sections:
  - block: about.biography
    id: about
    content:
      title: Biography
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
  - block: features
    content:
      title: Skills
      items:
        - name: Python
          description: 100%
          icon: python
          icon_pack: fab
        - name: Statistics
          description: 100%
          icon: chart-line
          icon_pack: fas
        - name: Node
          description: 100%
          icon: node
          icon_pack: fab
        - name: React
          description: 100%
          icon: react
          icon_pack: fab
        - name: Archeology
          description: 100%
          icon: hat-cowboy
          icon_pack: fas
  - block: experience
    content:
      title: Experience
      # Date format for experience
      #   Refer to https://wowchemy.com/docs/customization/#date-format
      date_format: Jan 2006
      # Experiences.
      #   Add/remove as many `experience` items below as you like.
      #   Required fields are `title`, `company`, and `date_start`.
      #   Leave `date_end` empty if it's your current employer.
      #   Begin multi-line descriptions with YAML's `|2-` multi-line prefix.
      items:
        - title: Vice President, Global Architecture, Risk and Data
          company: Manulife
          company_url: ''
          company_logo: manulife
          location: Massachusetts
          date_start: '2021-03-01'
          date_end: ''
          description: |2-
              Shawn McCarthy has been serving as the Vice President of Global Architecture, Risk, and Data at Manulife since March 2020. Leveraging his extensive background in software development, organizational development, and solution architecture, he has been instrumental in navigating the challenges of global architecture, risk management, and data handling in various regions including North America, Asia, and Europe. Manulife, being a Canadian multinational insurance company and financial services provider, can benefit immensely from Shawn's expertise. With his abilities to adapt to new technologies and situations, he can help in managing the company's vast portfolio of applications supporting a variety of sectors​. Manulife is the largest insurance company in Canada and the 28th largest fund manager in the world, with a strong presence in Canada, Asia, and the United States through its John Hancock Financial division​.
        - title: Graduate Instructor
          company: University of Colorado Denver
          company_url: ''
          company_logo: colorado
          location: Colorado
          date_start: '2015-01-01'
          date_end: ''
          description: |2-
              Shawn McCarthy has been affiliated with the University of Colorado Denver for over 9 years, serving in roles such as an advisory board member and a graduate instructor. As an advisory board member, he focuses on driving corporate relationships, expanding the university's community presence, developing programs for students, and encouraging faculty development. As a graduate instructor, he teaches courses in Web API technologies. His commitment to the university and its students, along with his industry experience and technical knowledge, make him a valuable asset. The University of Colorado Denver is a public research university that is part of the University of Colorado system. Its history dates back to 1912, and it is recognized for its urban campus that houses over 13,500 students
        - title: Managing Director - Platform and Application Architecture
          company: Charles Schwab
          company_url: ''
          company_logo: charles
          location: Colorado
          date_start: '2016-09-01'
          date_end: '2020-03-01'
          description:  |2-
              Shawn McCarthy served as the Managing Director of Platform and Application Architecture at Charles Schwab for nearly four years. He led Schwab's platform and application architecture team, oversaw the technology strategy for Schwab application technology, and was responsible for the solution architecture and digital strategy. His leadership and technical skills were crucial in shaping the current and future technology of the company to suit the ever-changing financial services industry. Charles Schwab is an American multinational financial services company offering banking, commercial banking, investing, consulting, and wealth management advisory services to both retail and institutional clients. It ranks tenth on the list of largest banks in the United States by assets and has over 400 branches, primarily in financial centers in the United States and the United Kingdom
    design:
      columns: '2'
  - block: accomplishments
    content:
      # Note: `&shy;` is used to add a 'soft' hyphen in a long heading.
      title: 'Accomplish&shy;ments'
      subtitle:
      # Date format: https://wowchemy.com/docs/customization/#date-format
      date_format: Jan 2006
      # Accomplishments.
      #   Add/remove as many `item` blocks below as you like.
      #   `title`, `organization`, and `date_start` are the required parameters.
      #   Leave other parameters empty if not required.
      #   Begin multi-line descriptions with YAML's `|2-` multi-line prefix.
      items:
        - certificate_url: https://courses.nvidia.com/certificates/5b642ef5f0a84d5bb92701dfcfde44f3/
          date_end: ''
          date_start: '2022-08-01'
          description: Instructor Materials - Applications of AI for Anomaly Detection
          organization: Nvidia
          organization_url: https://www.nvidia.com
          title: Applications of AI for Anomaly Detection
          url: ''
        - certificate_url: https://courses.nvidia.com/certificates/9a20d0076e4a44beb037551ebebe4891/
          date_end: ''
          date_start: '2022-06-01'
          description: Building Transformer-Based Natural Language Processing Applications (Instructor Materials)
          organization: Nvidia
          organization_url: https://www.nvidia.com
          title: Building Transformer-Based Natural Language Processing Applications 
          url: ''
        - certificate_url: https://courses.nvidia.com/certificates/d97fcd6c466d4171a3ff28c2e72609fe/
          date_end: ''
          date_start: '2022-05-01'
          description: Instructor Materials - Building Intelligent Recommender Systems
          organization: Nvidia
          organization_url: https://www.nvidia.com
          title: Building Intelligent Recommender Systems
          url: ''
    design:
      columns: '2'
#  - block: collection
#    id: posts
#    content:
#      title: Recent Posts
#      subtitle: ''
#      text: ''
#      # Choose how many pages you would like to display (0 = all pages)
#      count: 5
#      # Filter on criteria
#      filters:
#        folders:
#          - post
#        author: ""
#        category: ""
#        tag: ""
#        exclude_featured: false
#        exclude_future: false
#        exclude_past: false
#        publication_type: ""
#      # Choose how many pages you would like to offset by
#      offset: 0
#      # Page order: descending (desc) or ascending (asc) date.
#      order: desc
#    design:
#      # Choose a layout view
#      view: compact
#      columns: '2'
  - block: portfolio
    id: projects
    content:
      title: Projects
      filters:
        folders:
          - project
      # Default filter index (e.g. 0 corresponds to the first `filter_button` instance below).
      default_button_index: 0
      # Filter toolbar (optional).
      # Add or remove as many filters (`filter_button` instances) as you like.
      # To show all items, set `tag` to "*".
      # To filter by a specific tag, set `tag` to an existing tag name.
      # To remove the toolbar, delete the entire `filter_button` block.
      buttons:
        - name: All
          tag: '*'
        - name: Langchain
          tag: Langchain
        - name: Other
          tag: Demo
    design:
      # Choose how many columns the section has. Valid values: '1' or '2'.
      columns: '1'
      view: showcase
      # For Showcase view, flip alternate rows?
      flip_alt_rows: false
  #- block: markdown
  #  content:
  #    title: Gallery
  #    subtitle: ''
  #    text: |-
  #      {{< gallery album="demo" >}}
  #  design:
  #    columns: '1'
  - block: collection
    id: featured
    content:
      title: Featured Publications
      filters:
        folders:
          - publication
        featured_only: true
    design:
      columns: '2'
      view: card
  - block: collection
    content:
      title: Recent Publications
      text: |-
        {{% callout note %}}
        Quickly discover relevant content by [filtering publications](./publication/).
        {{% /callout %}}
      filters:
        folders:
          - publication
        exclude_featured: true
    design:
      columns: '2'
      view: citation
  - block: collection
    id: talks
    content:
      title: Recent & Upcoming Talks
      filters:
        folders:
          - event
    design:
      columns: '2'
      view: compact
  - block: tag_cloud
    content:
      title: Popular Topics
    design:
      columns: '2'
  - block: contact
    id: contact
    content:
      title: Contact
      subtitle:
      text: ''
      # Contact (add or remove contact options as necessary)
      email: shawn.mccarthy@ucdenver.edu
      phone: (303) 900-8613
      appointment_url: 'https://calendly.com/shawnemccarthy/30min'
      address:
        street: 1380 Lawrence Street, 8th floor
        city: Denver
        region: CO
        postcode: '80204'
        country: United States
        country_code: US
      directions: ''
      office_hours:
        - 'Monday 16:45 to 17:45'
        - 'Wednesday 16:45 to 17:45'
      contact_links:
        - icon: discord
          icon_pack: fab
          name: DM Me
          link: 'https://discordapp.com/users/shawnemccarthy/#6921'
        - icon: video
          icon_pack: fas
          name: Teams
          link: 'https://teams.microsoft.com'
      # Automatically link email and phone or display as text?
      autolink: true
    design:
      columns: '2'
---
