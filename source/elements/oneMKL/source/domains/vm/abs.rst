.. SPDX-FileCopyrightText: 2019-2020 Intel Corporation
..
.. SPDX-License-Identifier: CC-BY-4.0

.. _onemkl_vm_abs:

abs
===


.. container::


   Computes absolute value of vector elements.


   .. container:: section


      .. rubric:: Syntax
         :class: sectiontitle


      Buffer API:


      .. code-block:: cpp


            namespace oneapi::mkl::vm {

            sycl::event abs(
                    sycl::queue& exec_queue,
                    std::int64_t n,
                    sycl::buffer<T,1>& a,
                    sycl::buffer<R,1>& y,
                    oneapi::mkl::vm::mode mode = oneapi::mkl::vm::mode::not_defined);

            } // namespace oneapi::mkl::vm



      USM API:


      .. code-block:: cpp


            namespace oneapi::mkl::vm {

            sycl::event abs(
                    sycl::queue& exec_queue,
                    std::int64_t n,
                    const T *a,
                    R* y,
                    sycl::vector_class<sycl::event> const & depends = {},
                    oneapi::mkl::vm::mode mode = oneapi::mkl::vm::mode::not_defined);

            } // namespace oneapi::mkl::vm



      ``abs`` supports the following precisions.


      .. list-table::
         :header-rows: 1

         * - T
           - R
         * - ``float``
           - ``float``
         * - ``double``
           - ``double``
         * - ``std::complex<float>``
           - ``float``
         * - ``std::complex<double>``
           - ``double``




.. container:: section


   .. rubric:: Description
      :class: sectiontitle


   The abs(a) function computes an absolute value of vector elements.


   .. container:: tablenoborder


      .. list-table::
         :header-rows: 1

         * - Argument
           - Result
           - Status code
         * - +0
           - +0
           -  
         * - -0
           - +0
           -  
         * - +∞
           - +∞
           -  
         * - -∞
           - +∞
           -  
         * - QNAN
           - QNAN
           -  
         * - SNAN
           - QNAN
           -  




   Specifications for special values of the complex functions are defined
   according to the following formula


   ``abs(a) = hypot(RE(a), IM(a))``.


   The abs function does not generate any errors.


.. container:: section


   .. rubric:: Input Parameters
      :class: sectiontitle


   Buffer API:


   exec_queue
      The queue where the routine should be executed.


   n
      Specifies the number of elements to be calculated.


   a
      The buffer ``a`` containing input vector of size ``n``.


   mode
      Overrides the global VM mode setting for this function call. See
      :ref:`onemkl_vm_setmode`
      function for possible values and their description. This is an
      optional parameter. The default value is ``oneapi::mkl::vm::mode::not_defined``.


   USM API:


   exec_queue
      The queue where the routine should be executed.


   n
      Specifies the number of elements to be calculated.


   a
      Pointer ``a`` to the input vector of size ``n``.


   depends
      Vector of dependent events (to wait for input data to be ready).


   mode
      Overrides the global VM mode setting for this function call. See
      the :ref:`onemkl_vm_setmode`
      function for possible values and their description. This is an
      optional parameter. The default value is ``oneapi::mkl::vm::mode::not_defined``.


.. container:: section


   .. rubric:: Output Parameters
      :class: sectiontitle


   Buffer API:


   y
      The buffer ``y`` containing the output vector of size ``n``.


   USM API:


   y
      Pointer ``y`` to the output vector of size ``n``.


   return value (event)
      Event, signifying availability of computed output and status code(s).

.. container:: section


    .. rubric:: Exceptions
        :class: sectiontitle

    For list of generated exceptions please refer to  :ref:`onemkl_vm_exceptions`


.. container:: familylinks


   .. container:: parentlink

      **Parent topic:** :ref:`onemkl_vm_mathematical_functions`


