---
layout: default
title: Home
---

<div class="hero">
    <div class="container">
        <div class="hero-content">
            <h1 class="hero-title">Hello, I'm <span class="highlight">Bianca Surya Nobelia</span></h1>
            <p class="hero-description">
                Building real-world automation and embedded systems — from industrial machines and AGVs to humanoid robots and IoT monitoring.
            </p>
            <div class="hero-actions">
                <a href="{{ '/projects/' | relative_url }}" class="btn btn-primary">View My Projects</a>
                <a href="{{ '/contact/' | relative_url }}" class="btn btn-secondary">Get in Touch</a>
            </div>
        </div>
    </div>
</div>

<section class="section">
    <div class="container">
        <h2 class="section-title">About Me</h2>
        <div class="about-content">
            <p>
                A highly motivated and enthusiastic engineer with expertise in various aspects of automation and embedded systems, including Industrial Automation, Mechanical Design, IoT, HMI Development, Servo &amp; Pneumatic Systems, and Autonomous Robotics.
            </p>
            <p>
                I hold a track record of winning national robotics competitions and possess experience across full-time industry roles, internships, and academic research. Currently focusing on building my career in advanced robotics and embedded systems, while deepening my knowledge in system integration and autonomous systems.
            </p>
        </div>
    </div>
</section>

<section class="section section-alt">
    <div class="container">
        <h2 class="section-title">Featured Projects</h2>
        <div class="projects-grid">
            {% assign featured_projects = site.projects | where: "featured", true | limit: 3 %}
            {% if featured_projects.size > 0 %}
                {% for project in featured_projects %}
                <div class="project-card">
                    {% if project.cover_image %}
                    <div class="project-card-image">
                        {% if project.project_type %}
                            <span class="type-badge type-{{ project.project_type }}">
                            {% if project.project_type == "full-time" %}Full-time{% elsif project.project_type == "internship" %}Internship{% else %}Research{% endif %}
                            </span>
                        {% endif %}
                        <img src="{{ project.cover_image | relative_url }}" alt="{{ project.title }}">
                    </div>
                    {% endif %}
                    <div class="project-card-content">
                        <h3><a href="{{ project.url | relative_url }}">{{ project.title }}</a></h3>
                        <p>{{ project.description }}</p>
                        {% if project.tags %}
                        <div class="project-tags">
                            {% for tag in project.tags limit: 3 %}
                            <span class="tag">{{ tag }}</span>
                            {% endfor %}
                        </div>
                        {% endif %}
                        <a href="{{ project.url | relative_url }}" class="btn btn-small">View Project →</a>
                    </div>
                </div>
                {% endfor %}
            {% else %}
                <p class="text-center">No featured projects yet.</p>
            {% endif %}
        </div>
        <div class="text-center" style="margin-top: 2rem;">
            <a href="{{ '/projects/' | relative_url }}" class="btn btn-secondary">View All Projects</a>
        </div>
    </div>
</section>
