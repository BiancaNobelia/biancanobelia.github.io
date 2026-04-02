---
layout: page
title: Projects
subtitle: A collection of my work and side projects
permalink: /projects/
---

<div class="projects-filter">
    <p class="filter-label">Filter by:</p>
    <div class="filter-tags">
        <button class="filter-tag active" data-filter="all">All</button>
        <button class="filter-tag" data-filter="full-time">Full-time</button>
        <button class="filter-tag" data-filter="internship">Internship</button>
        <button class="filter-tag" data-filter="research">Research</button>
    </div>
    <p class="project-count"><span id="visible-count">{{ site.projects.size }}</span> project(s)</p>
</div>

<div class="projects-grid">
    {% if site.projects.size > 0 %}
        {% for project in site.projects %}
        <div class="project-card" data-type="{{ project.project_type }}">
            {% if project.cover_image %}
            <div class="project-card-image">
                {% if project.project_type %}
                    <span class="type-badge type-{{ project.project_type }}">
                    {% if project.project_type == "full-time" %}Full-time Work{% elsif project.project_type == "internship" %}Internship{% else %}Research{% endif %}
                    </span>
                {% endif %}
                <a href="{{ project.url | relative_url }}">
                    <img src="{{ project.cover_image | relative_url }}" alt="{{ project.title }}">
                </a>
            </div>
            {% endif %}
            
            <div class="project-card-content">
                <h3>
                    <a href="{{ project.url | relative_url }}">{{ project.title }}</a>
                </h3>
                
                {% if project.description %}
                <p class="project-description">{{ project.description }}</p>
                {% endif %}
                
                {% if project.tags %}
                <div class="project-tags">
                    {% for tag in project.tags %}
                    <span class="tag">{{ tag }}</span>
                    {% endfor %}
                </div>
                {% endif %}
                
                <div class="project-card-footer">
                    <a href="{{ project.url | relative_url }}" class="btn btn-small">View Details →</a>
                </div>
            </div>
        </div>
        {% endfor %}
    {% else %}
        <div class="empty-state">
            <p>No projects yet. Create your first project by adding a Markdown file to the <code>_projects/</code> folder!</p>
        </div>
    {% endif %}
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
    const filterTags = document.querySelectorAll('.filter-tag');
    const projectCards = document.querySelectorAll('.project-card');
    const countEl = document.getElementById('visible-count');

    filterTags.forEach(tag => {
        tag.addEventListener('click', function() {
            const filter = this.getAttribute('data-filter');

            filterTags.forEach(t => t.classList.remove('active'));
            this.classList.add('active');

            let visible = 0;
            projectCards.forEach(card => {
                const type = card.getAttribute('data-type');
                const show = filter === 'all' || type === filter;
                card.style.display = show ? 'block' : 'none';
                if (show) visible++;
            });

            if (countEl) countEl.textContent = visible;
        });
    });
});
</script>
