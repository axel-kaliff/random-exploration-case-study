---
title: 'Home'
date: 2023-10-24
type: landing

design:
  spacing: "6rem"

sections:

  - block: markdown
    content:
      text: |
        <center>
        <div class="custom-hero">
          <h2>Can Visuo-motor Policies Benefit From Random Exploration Data?</h2>
          <h3>A Case Study on Stacking</h3>
          <p class="authors">Shutong Jin*, Axel Kaliff*, Ruiyu Wang, Muhammad Zahid, Florian T. Pokorny</p>
        </div>
          <a
            href="https://arxiv.org/abs/2503.23571"
            class="inline-block rounded border px-5 py-2 font-semibold transition
            md:ml-4 px-4 py-1.5 text-sm
            border-black  hover:bg-black dark:hover:bg-white dark:hover:text-black hover:text-white dark:border-white dark:text-white dark:hover:bg-white
            hidden lg:inline-block">
            Read the Paper
          </a>
          <a href="https://github.com/ShutongJIN/CloudGripper_Stack_1k" class="mt-3 inline-flex items-center text-white bg-primary-700 hover:bg-primary-800 focus:ring-4 focus:ring-primary-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:focus:ring-primary-900">
            Explore the Code
            <svg class="ml-2 -mr-1 w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
          </a>
        </center>
 
    design:
      css_class: "dark"
      css_style: |
        .custom-hero {
          padding: 4rem 2rem;
          text-align: center;
          color: white;
        }
        .custom-hero h2 {
          font-size: 2.5rem;
          font-weight: 700;
          margin-bottom: 0.5rem;
        }
        .custom-hero h3 {
          font-size: 1.5rem;
          font-weight: 500;
          margin-bottom: 1rem;
        }
        .custom-hero .authors {
          font-size: 1rem;
          margin-bottom: 1.5rem;
        }
        .buttons {
          display: flex;
          justify-content: center;
          gap: 1rem;
          margin-top: 2rem;
        }
        .primary-button, .secondary-button {
          display: inline-block;
          padding: 0.7rem 1.5rem;
          border-radius: 20px;
          font-weight: 500;
          text-decoration: none;
          transition: all 0.3s ease;
          border: 1px solid #6a0dad;
        }
        .primary-button {
          background-color: #6a0dad;
          color: white;
        }
        .secondary-button {
          background-color: rgba(106, 13, 173, 0.7);
          color: white;
        }
        .primary-button:hover, .secondary-button:hover {
          transform: translateY(-2px);
          box-shadow: 0 4px 8px rgba(106, 13, 173, 0.3);
          background-color: #7b1fa2;
        }
      background:
        color: "navy"
        image:
          filename: matrix.gif
          filters:
            brightness: 0.11

  - block: stats
    content:
      items:
        - statistic: "13k+"
          description: |
            Real-world experiments performed
        - statistic: "750+"
          description: |
            Hours of labeled robot activity data
        - statistic: "1200+"
          description: |
            Policy evaluations conducted
    design:
      css_class: "bg-gray-100 dark:bg-gray-900"
      spacing:
        padding: ["1rem", 0, "1rem", 0]

  - block: markdown
    content:
      text: |
        ## Overview
        This work examines two paradigms for leveraging random exploration data in visuo-motor policy learning. In **Paradigm I**, random exploration video frames are used for self-supervised visual pre-training employing various objective functions. In **Paradigm II**, random motor commands are utilized within a **staged learning framework** to autonomously collect data for behavior cloning. This study presents a dataset comprising over **750 hours** of robot data, offering insights into the benefits and limitations of each approach.
    design:
      css_class: "light"
      css_style: |
        h2 {
          font-size: 2rem;
          margin-bottom: 1rem;
        }
        p {
          font-size: 1rem;
          line-height: 1.6;
        }
      background:
        color: "white"

  - block: cta-image-paragraph
    id: solutions
    content:
      items:
        - title: Random Video Frames for Visual Pre-training
          text: |
            Paradigm I utilizes unstructured video data from the CloudGripper-Push-1K dataset to pre-train visual encoders. This approach aims to leverage dynamic environmental interactions for improved visuo-motor policy performance. The performance of policies using encoders pre-trained on the CloudGripper-Push-1K dataset is compared to policies trained on other datasets, including ImageNet and the Days of Hands dataset.
          image: structureA.png
          button:
            text: CloudGripper-Push-1K Dataset
            url: "https://github.com/cloudgripper/cloudgripper-push-1k"
        - title: Random Motor Commands for Staged Learning
          text: |
            Paradigm II implements a staged learning framework where random motor commands generate training episodes which are used to train a policy, which in turn gathers more training data. This work compares different methods of implementing this paradigm, including using separate policies for subtasks.
          feature_icon: bolt
          image: structureB.png
          button:
            text: Explore Pipeline
            url: "https://github.com/ShutongJIN/CloudGripper_Stack_1k"
    design:
      css_class: "bg-gray-100 dark:bg-gray-900"
      spacing:
        padding: ["2rem", "2rem", "2rem", "2rem"]

  - block: features
    id: features
    content:
      title: Comparative Analysis of Self-Supervised Objective Functions
      text: Explore how different pre-training methods impact visuo-motor policy performance. GIFs below show FullGrad saliency maps for the respective models with different pre-training objectives.
      items:
        - name: MoCo (Contrastive Loss)
          description: |
            ![Alt text](moco_vit_small_RM_cam.gif)Our experiments indicate that MoCo pre-training results in **lower prediction errors** and **improved success rates**, though its performance is **sensitive to the initial object positions**.
        - name: DINO (Distillation Loss)
          description: |
            ![Alt text](dino_vit_small_RM_cam.gif)This model demonstrated **lower performance** on unstructured random data compared to MoCo, suggesting that **further tuning** is required.
        - name: MAE (Reconstruction Loss)
          description: |
            ![Alt text](mae_vit_small_RM_cam.gif)This model showed a **sensitivity to background clutter**, leading to **suboptimal performance** on random exploration frames in our stacking task.
    design:
      css_class: "bg-white dark:bg-gray-800"
      spacing:
        padding: ["2rem", "2rem", "2rem", "2rem"]

  - block: markdown
    content:
      text: |
        ## CloudGripper-Stack-750 Dataset
        ![Alt text](matrix.gif)
        The dataset comprises over **750 hours** of robot activity data—including **400 successful** and **12,000 failed** episodes—collected autonomously using the CloudGripper testbed. This comprehensive collection is provided as a resource for research on visuo-motor policy development. [Explore Dataset](https://github.com/ShutongJIN/CloudGripper_Stack_1k)
    design:
      css_class: "light"
      css_style: |
        h2 {
          font-size: 2rem;
          margin-bottom: 1rem;
        }
        p, a {
          font-size: 1rem;
          line-height: 1.6;
        }
      background:
        color: "white"


  - block: cta-card
    content:
      title: Collected Using CloudGripper
      text: |
          In this study, the **CloudGripper robotic testbed** was employed to remotely and autonomously collect a large dataset of real robot data, train policies, and conduct evaluations with **minimal human intervention** via cloud services. Researchers interested in utilizing CloudGripper are encouraged to explore the **open-source dataset** and **data collection pipeline**.
      button:
        text: CloudGripper Github
        url: "https://cloudgripper.org/getstarted"
    design:
      card:
        css_class: "bg-primary-700"
        css_style: "color: white; text-align: center; padding: 2rem;"

  - block: markdown
    content:
      text: |
        ### Acknowledgements
        \***Equal contribution.** The authors are with the School of Electrical Engineering and Computer Science, **KTH Royal Institute of Technology**. This work was partially supported by the **Wallenberg AI, Autonomous Systems and Software Program (WASP)**, funded by the Knut and Alice Wallenberg Foundation. The computations were enabled by the supercomputing resource Berzelius provided by the National Supercomputer Centre at Linköping University and the Knut and Alice Wallenberg Foundation, Sweden.
        ![Alt text](kth-logo.png) ![Alt text](wasp-logo.png)
    design:
      css_class: "light"
      css_style: |
        h2 {
          font-size: 2rem;
          margin-bottom: 1rem;
        }
        p, a {
          font-size: 0.5rem;
          line-height: 1.6;
        }
      background:
        color: "white"
---
